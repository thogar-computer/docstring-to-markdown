# docstring2md
## Description:

This package Export Google DocString to Markdown from Python module.

## Setup:
```shell
$ git clone https://github.com/francois-le-ko4la/docstring-to-markdown.git
$ cd docstring-to-markdown
$ make install
```

## Test:

This module has been tested and validated on Ubuntu 17.10/18.04.
```shell
$ make test
```

## Use:

Use the script:
```shell
$ export_docstring2md.py -h
usage: export_docstring2md.py [-h] [-v] -i INPUT [-o FILE] [-t FILE] [-r FILE]
                              [-uml FILE] [--toc | --no-toc]

This script is provided by docstring2md package.
It exports google docstrings from python module to a Markdown file in order to
generate README.

optional arguments:
  --toc                 Enable the table of contents (DEFAULT)
  --no-toc              Disable the table of contents

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit

required arguments:
  -i INPUT, --input INPUT
                        Input file name

optional arguments:
  -o FILE, --output FILE
                        Output file
  -t FILE, --runtime FILE
                        Runtime file
  -r FILE, --requirements FILE
                        requirements.txt file
  -uml FILE, --uml-diagramm FILE
                        UML file (PNG)

Enjoy...
```

## Project structure

```
.
├── bin
│   └── export_docstring2md.py
├── docstring2md
│   ├── __about__.py
│   ├── doc2md.py
│   ├── __init__.py
│   └── main.py
├── LICENSE
├── Makefile
├── MANIFEST.in
├── pictures
│   ├── classes_docstring2md.png
│   └── packages_docstring2md.png
├── README.md
├── requirements.txt
├── runtime.txt
├── setup.cfg
├── setup.py
└── tests
    ├── test_docstring2md.py
    ├── test_doctest.py
    └── test_pycodestyle.py
```

## Todo:

- [X] Create the project
- [X] Write code and tests
- [X] Test installation and requirements (setup.py and/or Makefile)
- [X] Test code
- [X] Validate features
- [X] Add-on : decorator
- [X] Add-on : class properties
- [X] Add-on : runtime & requirements
- [X] Add-on : toc
- [ ] Write Doc/stringdoc
- [X] Run PEP8 validation
- [ ] Clean & last check
- [ ] Release

## License

This package is distributed under the [GPLv3 license](./LICENSE)
## Dev notes
### Runtime

```
python-3.6.x

```
### Requirements

```
setuptools>=36.2.7
pycodestyle>=2.3.1

```
### UML Diagram
![alt text](pictures/classes_docstring2md.png)

### Objects
[ConvMD()](#convmd)<br />
[ConvMD.add_tag(begin_tag, end_tag)](#convmdadd_tagbegin_tag-end_tag)<br />
[ConvMD.repl_beg_end(begin_regexp, end_regexp, begin_tag, end_tag)](#convmdrepl_beg_endbegin_regexp-end_regexp-begin_tag-end_tag)<br />
[ConvMD.repl_str(old_string, new_string)](#convmdrepl_strold_string-new_string)<br />
[DocString2MD()](#docstring2md)<br />
[@Property: DocString2MD.module_name](#property-docstring2mdmodule_name)<br />
[DocString2MD.get_doc(self)](#docstring2mdget_docself)<br />
[DocString2MD.import_module(self)](#docstring2mdimport_moduleself)<br />
[DocStringObj()](#docstringobj)<br />
[@Property: DocStringObj.value](#property-docstringobjvalue)<br />
[ExtractPythonModule()](#extractpythonmodule)<br />
[ExtractPythonModule.extract(self)](#extractpythonmoduleextractself)<br />
[ExtractPythonModule.import_module(self)](#extractpythonmoduleimport_moduleself)<br />
[LineType()](#linetype)<br />
[MembersObj()](#membersobj)<br />
[MembersObj.items(self)](#membersobjitemsself)<br />
[MembersObj.sortkeys(self)](#membersobjsortkeysself)<br />
[ModuleObj()](#moduleobj)<br />
[ModuleObj.getallstr(self, member=None)](#moduleobjgetallstrself-membernone)<br />
[ModuleObj.gettoc(self, member=None)](#moduleobjgettocself-membernone)<br />
[PythonObj.getlink(self)](#pythonobjgetlinkself)<br />
[MyConst()](#myconst)<br />
[PythonDefinitionObj()](#pythondefinitionobj)<br />
[@Property: PythonDefinitionObj.value](#property-pythondefinitionobjvalue)<br />
[PythonObj()](#pythonobj)<br />
[PythonObj.getlink(self)](#pythonobjgetlinkself)<br />
[PythonObjType()](#pythonobjtype)<br />
[ReadFile()](#readfile)<br />
[@Property: ReadFile.filename](#property-readfilefilename)<br />
[ReadFile.get(self)](#readfilegetself)<br />
[ReadFile.isdefined(self)](#readfileisdefinedself)<br />
[Tag()](#tag)<br />
[TitleObj()](#titleobj)<br />
[@Property: TitleObj.level](#property-titleobjlevel)<br />
[@Property: TitleObj.title](#property-titleobjtitle)<br />
[TitleObj.getanchor(self)](#titleobjgetanchorself)<br />
[wraps(wrapped, assigned=('__module__', '__name__', '__qualname__', '__doc__', '__annotations__'), updated=('__dict__',))](#wrapswrapped-assigned__module__-__name__-__qualname__-__doc__-__annotations__-updated__dict__)<br />


#### ConvMD()
```python
class ConvMD(object):
```

```
Prepare MD string
```

##### ConvMD.add_tag(begin_tag, end_tag)
```python
def ConvMD.add_tag(begin_tag, end_tag):
```
> <br />
> Decorator - add a tag<br />
> <br />
> <b>Example:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  ('__', '__') => __ TXT __<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  beg_tag (str)<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  end_tag (str)<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  decorated function<br />
> <br />
##### ConvMD.repl_beg_end(begin_regexp, end_regexp, begin_tag, end_tag)
```python
def ConvMD.repl_beg_end(begin_regexp, end_regexp, begin_tag, end_tag):
```
> <br />
> Decorator - replace the beggining and the end<br />
> <br />
> <b>Example:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  All new lines must be provided with a specific tag<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  > 'Line' <br /><br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  begin_regexp (str)<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  end_regexp (str)<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  begin_tag (str)<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  end_tag (str)<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  decorated function<br />
> <br />
##### ConvMD.repl_str(old_string, new_string)
```python
def ConvMD.repl_str(old_string, new_string):
```
> <br />
> Decorator - search & replace a string by another string<br />
> Example : replace space by a HTML tag.<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  old_string (str): string to search<br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  new_string (str): new string<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  decorated function<br />
> <br />
#### DocString2MD()
```python
class DocString2MD(object):
```

```
Class DocString2MD : export Google docstring to MD File.

Use:
    >>> doc = DocString2MD("docstring2md")
    >>> doc.import_module()
    True
    >>> result = doc.get_doc()
    >>> result = result.split("\n")
    >>> print(result[0])
    # docstring2md
```

##### @Property: DocString2MD.module_name
```python
@property
def DocString2MD.module_name(self):
@module_name.setter
def DocString2MD.module_name(self, module_name):

```
> <br />
> return /path/to/the/json/file<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
##### DocString2MD.get_doc(self)
```python
def DocString2MD.get_doc(self):
```
> <br />
> Extract the doc<br />
> Returns self.__output or self.__writedoc<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  str: self.__output<br />
> <br />
##### DocString2MD.import_module(self)
```python
def DocString2MD.import_module(self):
```
> <br />
> Docstring empty<br />
> <br />
#### DocStringObj()
```python
class DocStringObj(object):
```

```
String to store and prepare the docstring.
This object will become an attribut.

Use:
    >>> docstring = DocStringObj("My docstring", PythonObjType.fun)
    >>> print(docstring)
    > <br />
    > My docstring<br />
    > <br />
    >>> docstring = DocStringObj("", PythonObjType.fun)
    >>> print(docstring)
    > <br />
    > <br />
    > <br />
    >>> docstring = DocStringObj("My docstring", PythonObjType.cla)
    >>> print(docstring)
    <BLANKLINE>
    ```
    My docstring
    ```
    <BLANKLINE>
```

##### @Property: DocStringObj.value
```python
@property
def DocStringObj.value(self):
@value.setter
def DocStringObj.value(self, value):

```
> <br />
> @Property<br />
> <br />
#### ExtractPythonModule()
```python
class ExtractPythonModule(object):
```

```
Object in order to extract Python functions, classes....

Use:
    >>> mod = ExtractPythonModule("oups...")
    >>> mod.import_module()
    Traceback (most recent call last):
    ...
    ModuleNotFoundError: No module named 'oups'
    >>> mod = ExtractPythonModule("json")
    >>> mod.import_module()
    True
    >>> mod.extract()
```

##### ExtractPythonModule.extract(self)
```python
def ExtractPythonModule.extract(self):
```
> <br />
> Defines module object and extracts all members.<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
##### ExtractPythonModule.import_module(self)
```python
@__check_module
def ExtractPythonModule.import_module(self):
```
> <br />
> Check module<br />
> Import the module via the passed in module specification<br />
> Returns the newly imported module and updates attributes self.__module<br />
> <br />
> <b>Args:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  None<br />
> <br />
> <b>Returns:</b><br />
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  bool: The return value. True for success, False otherwise.<br />
> <br />
#### LineType()
```python
class LineType:
```

```
Docstring empty
```

#### MembersObj()
```python
class MembersObj(object):
```

```
Dict() to store a python object's members.
This object will become an attribute.
```

##### MembersObj.items(self)
```python
def MembersObj.items(self):
```
> <br />
> Docstring empty<br />
> <br />
##### MembersObj.sortkeys(self)
```python
def MembersObj.sortkeys(self):
```
> <br />
> Docstring empty<br />
> <br />
#### ModuleObj()
```python
class ModuleObj(PythonObj):
```

```
Class in order to register module informations
__str__ is used to export with MD format.

Use:
    >>> obj = ModuleObj("Mod", "module", "mod doc")
    >>> print(obj)
    mod doc
    ## Dev notes
    <BLANKLINE>
```

##### ModuleObj.getallstr(self, member=None)
```python
def ModuleObj.getallstr(self, member=None):
```
> <br />
> Docstring empty<br />
> <br />
##### ModuleObj.gettoc(self, member=None)
```python
def ModuleObj.gettoc(self, member=None):
```
> <br />
> Docstring empty<br />
> <br />
##### PythonObj.getlink(self)
```python
def PythonObj.getlink(self):
```
> <br />
> Docstring empty<br />
> <br />
#### MyConst()
```python
class MyConst:
```

```
Docstring empty
```

#### PythonDefinitionObj()
```python
class PythonDefinitionObj(object):
```

```
String so store and prepare the object definition:
Example : def function_name(*args)
This object will become an attribute.

Use:
    >>> obj = PythonDefinitionObj(1)
    Traceback (most recent call last):
    ...
    ValueError: PytDefObj: bad value
    >>> obj = PythonDefinitionObj("")
    Traceback (most recent call last):
    ...
    ValueError: PytDefObj: bad value
    >>> obj = PythonDefinitionObj("MyOBJ")
    >>> print(obj)
    ```python
    MyOBJ
    ```
```

##### @Property: PythonDefinitionObj.value
```python
@property
def PythonDefinitionObj.value(self):
@value.setter
def PythonDefinitionObj.value(self, value):

```
> <br />
> @Property<br />
> <br />
#### PythonObj()
```python
class PythonObj(object):
```

```
Class in order to register object informations
__str__ is used to export with MD format.

Use:
    >>> obj = PythonObj("Mc", "def Mc()", "Doc", 1, PythonObjType.fun)
    >>> print(obj)
    <BLANKLINE>
    #### Mc
    ```python
    def Mc()
    ```
    > <br />
    > Doc<br />
    > <br />
    >>> obj = PythonObj("Mc", "class Mc():", "Doc", 1, PythonObjType.cla)
    >>> print(obj)
    <BLANKLINE>
    #### Mc
    ```python
    class Mc():
    ```
    <BLANKLINE>
    ```
    Doc
    ```
    <BLANKLINE>
```

##### PythonObj.getlink(self)
```python
def PythonObj.getlink(self):
```
> <br />
> Docstring empty<br />
> <br />
#### PythonObjType()
```python
class PythonObjType:
```

```
Docstring empty
```

#### ReadFile()
```python
class ReadFile(object):
```

```
This class check if file exists and read the content

Use:
    >>> myfile = ReadFile("oups")
    Traceback (most recent call last):
    ...
    OSError: File not found ! (oups)
    >>> myfile = ReadFile("/etc/fstab")
    >>> print(myfile.isdefined())
    True
    >>>
```

##### @Property: ReadFile.filename
```python
@property
def ReadFile.filename(self):
@filename.setter
def ReadFile.filename(self, filename):

```
> <br />
> @Property<br />
> <br />
##### ReadFile.get(self)
```python
def ReadFile.get(self):
```
> <br />
> open & read the file<br />
> Returns the content<br />
> <br />
##### ReadFile.isdefined(self)
```python
def ReadFile.isdefined(self):
```
> <br />
> Docstring empty<br />
> <br />
#### Tag()
```python
class Tag:
```

```
Docstring empty
```

#### TitleObj()
```python
class TitleObj(object):
```

```
String to store and prepare MD title
This object will become an attribute.

Use:
    >>> title = TitleObj(3, "oups")
    Traceback (most recent call last):
    ...
    ValueError: TitleObj: Title type is string
    >>> title = TitleObj("Test_def(self, var, indx)", 3)
    >>> print(title)
    ###### Test_def(self, var, indx)
    >>> print(title.getanchor())
    test_defself-var-indx
```

##### @Property: TitleObj.level
```python
@property
def TitleObj.level(self):
@level.setter
def TitleObj.level(self, level):

```
> <br />
> @Property<br />
> <br />
##### @Property: TitleObj.title
```python
@property
def TitleObj.title(self):
@title.setter
def TitleObj.title(self, title):

```
> <br />
> @Property<br />
> <br />
##### TitleObj.getanchor(self)
```python
def TitleObj.getanchor(self):
```
> <br />
> Docstring empty<br />
> <br />
#### wraps(wrapped, assigned=('__module__', '__name__', '__qualname__', '__doc__', '__annotations__'), updated=('__dict__',))
```python
def wraps(wrapped, assigned=('__module__', '__name__', '__qualname__', '__doc__', '__annotations__'), updated=('__dict__',)):
```
> <br />
> Decorator factory to apply update_wrapper() to a wrapper function<br />
> <br />
> Returns a decorator that invokes update_wrapper() with the decorated<br />
> function as the wrapper argument and the arguments to wraps() as the<br />
> remaining arguments. Default arguments are as for update_wrapper().<br />
> This is a convenience function to simplify applying partial() to<br />
> update_wrapper().<br />
> <br />
