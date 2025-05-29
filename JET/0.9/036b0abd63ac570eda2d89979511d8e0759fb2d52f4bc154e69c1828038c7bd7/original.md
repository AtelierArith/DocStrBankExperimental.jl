```
@test_opt [jetconfigs...] [broken=false] [skip=false] f(args...)
```

Runs [`@report_opt jetconfigs... f(args...)`](@ref @report_opt) and tests that the function call `f(args...)` is free from optimization failures and unresolved method dispatches that `@report_opt` can detect.

As with [`@report_opt`](@ref), the [general configurations](@ref) and [optimization analysis specific configurations](@ref optanalysis-config) can be specified as an optional argument:

```julia-repl
julia> function f(n)
            r = sincos(n)
            # `println` is full of runtime dispatches,
            # but we can ignore the corresponding reports from `Base`
            # with the `target_modules` configuration
            println(r)
            return r
       end;

julia> @test_opt target_modules=(@__MODULE__,) f(10)
Test Passed
  Expression: #= REPL[3]:1 =# JET.@test_call analyzer = JET.OptAnalyzer target_modules = (#= REPL[3]:1 =# @__MODULE__(),) f(10)
```

Like [`@test_call`](@ref), `@test_opt` is fully integrated with the [`Test` standard library](https://docs.julialang.org/en/v1/stdlib/Test/). See [`@test_call`](@ref) for the details.
