```
runtests(files; subs = common_subs(), mod = nothing, quiet = false, exitfirst = false, maxfail = nothing) :: Bool
```

Load the specified Markdown files to extract and run the embedded test cases. When a directory is passed, load all `*.md` files in the directory.  This function returns `true` if the testing is successful, `false` otherwise.

Specify `subs` to customize substitutions applied to the expected output in order to convert it to a regular expression.

Specify `mod` to execute tests in the context of the given module.

Set `quiet = true` to suppress all output except for error reports.

Set `exitfirst = true` to exit on first error or failure.  Alternatively, use `maxfail` to set maximum allowable number of errors or failures.

```
runtests(; default = common_args(), subs = common_subs(), mod = nothing, quiet = false, exitfirst = false, maxfail = nothing)
```

In this form, test files are specified as command-line parameters.  When invoked without parameters, tests are loaded from `*.md` files in the program directory, which can be overriden using `default` parameter.  This function terminates the program with code `0` if the testing is successful, `1` otherwise.

Use this form in `test/runtests.jl`:

```julia
using NarrativeTest
NarrativeTest.runtests()
```
