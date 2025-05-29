```
@test_throws_wrapped exception expr
```

Similar to `Test.@test_throws`, but this tests that the expression `expr` either throws `exception`, OR that it throws an expression *wrapping* `exception`.

Users can use this function if they aren't concerned about whether an exception is wrapped or not, e.g. not caring whether the user is using concurrency.

# Examples

```jldoctest
julia> @test_throws_wrapped BoundsError [1, 2, 3][4]
Test Passed
      Thrown: BoundsError

julia> @test_throws_wrapped DimensionMismatch fetch(@async [1, 2, 3] + [1, 2])
Test Passed
      Thrown: DimensionMismatch
```
