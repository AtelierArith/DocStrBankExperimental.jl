```
runtests(; options=nothing, ignore_commandline=false)
```

Run the test suite.

This function has several side effects:

  * it parses the command-line arguments, using them to build the dictionary of run options (see [Run options](@ref run_options_manual) in the manual for the list);
  * it picks up and includes the test files, selected according to the options.

`options` must be a dictionary with the keys corresponding to some of the options from the above list. If `options` is given, command-line arguments are not parsed.

If `ignore_commandline` is `true`, command-line arguments passed to the program will not be used. This option can be helpful if one wants to be sure that the run options used are exactly the ones specified in the call.

Returns `0` if there are no failed tests, `1` otherwise.
