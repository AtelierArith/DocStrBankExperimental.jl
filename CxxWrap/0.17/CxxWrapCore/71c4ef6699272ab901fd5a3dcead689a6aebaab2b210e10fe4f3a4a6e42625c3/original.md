@readmodule libraryfile_cb [functionname]

Read a C++ module and associate it with the Julia module enclosing the macro call. `libraryfile_cb` is a function that returns the shared library file to load as a string. In case of a JLL exporting `libfoo.so` it is possible to use `foo_jll.get_libfoo_path()`
