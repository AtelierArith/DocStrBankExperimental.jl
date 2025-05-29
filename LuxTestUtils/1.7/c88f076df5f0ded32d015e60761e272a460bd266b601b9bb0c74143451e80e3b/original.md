```
@jet f(args...) call_broken=false opt_broken=false
```

Run JET tests on the function `f` with the arguments `args...`. If `JET.jl` fails to compile, then the macro will be a no-op.

## Keyword Arguments

  * `call_broken`: Marks the test_call as broken.
  * `opt_broken`: Marks the test_opt as broken.

All additional arguments will be forwarded to `JET.@test_call` and `JET.@test_opt`.

!!! tip
    Instead of specifying `target_modules` with every call, you can set global target modules using [`jet_target_modules!`](@ref).

    ```julia
    using LuxTestUtils

    jet_target_modules!(["Lux", "LuxLib"]) # Expects Lux and LuxLib to be present in the module calling `@jet`
    ```


## Example

```jldoctest
julia> @jet sum([1, 2, 3]) target_modules=(Base, Core)
Test Passed

julia> @jet sum(1, 1) target_modules=(Base, Core) opt_broken=true call_broken=true
Test Broken
  Expression: #= REPL[21]:1 =# JET.@test_opt target_modules = (Base, Core) sum(1, 1)
```
