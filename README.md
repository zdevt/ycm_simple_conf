YouCompleteMe Simple Configuration
==================================

Description
-----------

If you developp in C/C++ with Vim you probably know the great plugin
[YouCompleteMe](https://github.com/Valloric/YouCompleteMe).

In order to get it work you have to write a `.ycm_extra_conf.py` python script
and put it in your project directory. This script should provide needed
informations to compile your project. It is very tedious to copy it
each time you create a new project, because you just have to modify
a few part of it.

The solution proposed here is to keep a single python script
and at each project creation write a `.ycm_simple_conf.xml` file that
contain only project-specific informations:

```xml
<project type="c++">
    <include path="/home/local/libA/include"/>
    <include path="/home/local/libB/include"/>
    <include path="include"/>
    <include path="build"/>
</project>
```

Installation
------------

Use the great plugin [NeoBundle](https://github.com/Shougo/neobundle.vim)
and just add this line in the appropriate section of your `.vimrc` file:

    NeoBundle "tdcdev/ycm_simple_conf"

That's it ! Now if you want disable `ycm_simple_conf` add this line in
your `.vimrc` file:

    let g:ycm_simple_conf_active = 0

Usage
-----

As you can see above, it is very easy to write the `.ycm_simple_conf.xml` file.
Project type can be **c** or **c++**, and include path can be absolute or
relative to the `.ycm_simple_conf.xml` file.

It is not necessary to add default compiler include paths, `ycm_simple_conf.py`
ask compiler for them.

You can see witch flags are set with logfiles in `/tmp/ycm/` on Linux.
