@wrapmodule libraryfile_cb [functionname]

Place the functions and types from the C++ lib into the module enclosing this macro call Calls an entry point named `define_julia_module`, unless another name is specified as the second argument.

`libraryfile_cb` is a function that returns the shared library file to load as a string. In case of a JLL exporting `libfoo.so` it is possible to use `foo_jll.get_libfoo_path()`
