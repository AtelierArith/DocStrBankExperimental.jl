```
@test_all ex
@test_all f(args...) key=val ...
@test_all ex broken=true
@test_all ex skip=true
```

Test that the expression `all(ex)` evaluates to `true`. Does not short-circuit at  the first `false` value, so that all `false` elements are shown in case of failure.

Same return behaviour as [`Test.@test`](@extref Julia), namely: if executed inside a `@testset`, returns a `Pass` `Result` if `all(ex)` evaluates to `true`, a `Fail` `Result` if it evaluates to `false` or `missing`, and an `Error` `Result` if it could not be  evaluated. If executed outside a `@testset`, throws an exception instead of returning  `Fail` or `Error`.

# Examples

```@julia-repl
julia> @test_all [1.0, 2.0] .== [1, 2]
Test Passed

julia> @test_all [1, 2, 3] .< 2
Test Failed at none:1
  Expression: all([1, 2, 3] .< 2)
   Evaluated: false
    Argument: 3-element BitVector, 2 failures:
              [2]: 2 < 2 ===> false
              [3]: 3 < 2 ===> false
```

Similar to `@test`, the `@test_all f(args...) key=val...` form is equivalent to writing  `@test_all f(args...; key=val...)` which can be useful when the expression is a call using infix syntax such as vectorized approximate comparisons: 

```@julia-repl
julia> v = [0.99, 1.0, 1.01];

julia> @test_all v .≈ 1 atol=0.1
Test Passed
```

This is equivalent to the uglier test `@test_all .≈(v, 1, atol=0.1)`.  Keyword splicing also works through any negation operator:

```@julia-repl
julia> @test_all .!(v .≈ 1) atol=0.001
Test Failed at none:1
  Expression: all(.!.≈(v, 1, atol=0.001))
   Evaluated: false
    Argument: 3-element BitVector, 1 failure:
              [2]: !≈(1.0, 1, atol=0.001) ===> false

```

As with `@test`, it is an error to supply more than one expression unless  the first is a call (possibly broadcast `.` syntax) and the rest are  assignments (`k=v`).

The macro supports `broken=true` and `skip=true` keywords, with similar behavior  to [`Test.@test`](@extref Julia):

```@julia-repl
julia> @test_all [1, 2] .< 2 broken=true
Test Broken
  Expression: all([1, 2] .< 2)

julia> @test_all [1, 2] .< 3 broken=true
Error During Test at none:1
 Unexpected Pass
 Expression: all([1, 2] .< 3)
 Got correct result, please change to @test if no longer broken.

julia> @test_all [1, 2, 3] .< 2 skip=true
Test Broken
  Skipped: all([1, 2, 3] .< 2)
```
