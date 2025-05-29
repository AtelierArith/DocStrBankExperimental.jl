```
test_text(text::AbstractString; jetconfigs...)
test_text(text::AbstractString, filename::AbstractString; jetconfigs...)
```

Runs [`report_text`](@ref) and tests that there are no problems detected.

As with [`report_text`](@ref), the [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as an optional argument.

Like [`@test_call`](@ref), `test_text` is fully integrated with the [`Test` standard library](https://docs.julialang.org/en/v1/stdlib/Test/). See [`@test_call`](@ref) for the details.
