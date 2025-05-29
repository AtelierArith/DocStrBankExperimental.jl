```
test_package(package::Module; jetconfigs...)
test_package(package::AbstractString; jetconfigs...)
test_package(; jetconfigs...)
```

Runs [`report_package`](@ref) and tests that there are no problems detected.

As with [`report_package`](@ref), the [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as an optional argument.

Like [`@test_call`](@ref), `test_package` is fully integrated with the [`Test` standard library](https://docs.julialang.org/en/v1/stdlib/Test/). See [`@test_call`](@ref) for the details.

```julia
julia> @testset "test_package" begin
           test_package("Example"; toplevel_logger=nothing)
       end;
Test Summary: | Pass  Total  Time
test_package  |    1      1  0.0s
```
