```
init = read_init(fn)
init, raw_init = read_init(fn, extra_out = true)
```

Read a init file from `fn`. This should be the base path (i.e. without the `.RSRT` extension). The results are given as a Dict.

# Keyword arguments

  * `extra_out`: If true, return the raw Python object as well as the parsed data. Default is false.
  * `actnum=missing`: ACTNUM array that can be used to reduce the outputs to the active cells.

# Notes

This function requires the `resdata` Python package to be installed, which will be automatically added to your environment if you first install PythonCall and put `using PythonCall` in your script or REPL.

The main class to lookup on the Python side of things is `ResdataFile`.
