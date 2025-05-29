```
test_file(file::AbstractString; jetconfigs...)
```

Runs [`report_file`](@ref) and tests that there are no problems detected.

As with [`report_file`](@ref), the [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as an optional argument.

Like [`@test_call`](@ref), `test_file` is fully integrated with the [`Test` standard library](https://docs.julialang.org/en/v1/stdlib/Test/). See [`@test_call`](@ref) for the details.
