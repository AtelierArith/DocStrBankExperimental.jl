```
@test_call [jetconfigs...] [broken=false] [skip=false] f(args...)
```

Runs [`@report_call jetconfigs... f(args...)`](@ref @report_call) and tests that the function call `f(args...)` is free from problems that `@report_call` can detect. Returns a `Pass` result if the test is successful, a `Fail` result if any problems are detected, or an `Error` result if the test encounters an unexpected error. When the test `Fail`s, abstract call stack to each problem location will be printed to `stdout`.

```julia-repl
julia> @test_call sincos(10)
Test Passed
  Expression: #= none:1 =# JET.@test_call sincos(10)
```

As with [`@report_call`](@ref), the [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as an optional argument:

```julia-repl
julia> cond = false

julia> function f(n)
           # `cond` is untyped, and will be reported by the sound analysis pass,
           # while JET's default analysis pass will ignore it
           if cond
               return sin(n)
           else
               return cos(n)
           end
       end;

julia> @test_call f(10)
Test Passed
  Expression: #= none:1 =# JET.@test_call f(10)

julia> @test_call mode=:sound f(10)
JET-test failed at none:1
  Expression: #= none:1 =# JET.@test_call mode = :sound f(10)
  ═════ 1 possible error found ═════
  ┌ @ none:2 goto %4 if not cond
  │ non-boolean (Any) used in boolean context: goto %4 if not cond
  └──────────

ERROR: There was an error during testing
```

`@test_call` is fully integrated with [`Test` standard library](https://docs.julialang.org/en/v1/stdlib/Test/)'s unit-testing infrastructure. This means that the result of `@test_call` will be included in a final `@testset` summary and it supports `skip` and `broken` annotations, just like the `@test` macro:

```julia-repl
julia> using JET, Test

# Julia can't propagate the type constraint `ref[]::Number` to `sin(ref[])`, JET will report `NoMethodError`
julia> f(ref) = isa(ref[], Number) ? sin(ref[]) : nothing;

# we can make it type-stable if we extract `ref[]` into a local variable `x`
julia> g(ref) = (x = ref[]; isa(x, Number) ? sin(x) : nothing);

julia> @testset "check errors" begin
           ref = Ref{Union{Nothing,Int}}(0)
           @test_call f(ref)             # fail
           @test_call g(ref)             # fail
           @test_call broken=true f(ref) # annotated as broken, thus still "pass"
       end
check errors: JET-test failed at REPL[21]:3
  Expression: #= REPL[21]:3 =# JET.@test_call f(ref)
  ═════ 1 possible error found ═════
  ┌ f(ref::Base.RefValue{Union{Nothing, Int64}}) @ Main ./REPL[19]:1
  │ no matching method found `sin(::Nothing)` (1/2 union split): sin((ref::Base.RefValue{Union{Nothing, Int64}})[]::Union{Nothing, Int64})
  └────────────────────

Test Summary: | Pass  Fail  Broken  Total  Time
check errors  |    1     1       1      3  0.2s
ERROR: Some tests did not pass: 1 passed, 1 failed, 0 errored, 1 broken.
```
