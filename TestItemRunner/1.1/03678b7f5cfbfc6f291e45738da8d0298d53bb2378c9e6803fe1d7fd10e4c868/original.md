```
@run_package_tests(ex...)
```

Run all test items in a package, using optional filter and verbosity arguments.

# Usage

```julia
@run_package_tests filter=<filter_function>, verbose=<bool>
```

```julia
@run_package_tests filter=ti->!(:skipci in ti.tags)
```

# Arguments

  * `filter`: An optional filter function to apply to the test items.
  * `verbose`: An optional argument to specify verbosity.
