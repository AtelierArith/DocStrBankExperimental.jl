```
@testset_macro @mac
```

Declare `@mac` as a macro which must be expanded statically by `retest` so that contained `@testset`s can be discovered.

Consider this pattern with `Test` which factors out testsets in a function:

```julia
using Test

function test_iseven(x)
    @testset "iseven $x" begin
        @test iseven(x)
    end
end

@testset "test $x" for x=2:2:4
    test_iseven(x)
end
```

This doesn't translate directly with `ReTest`, as the call to `test_iseven` will be performed at run-time, and will end up declaring a new `@testset "iseven $x"` at toplevel (this is a problem similar to having `include` inside testsets). So on the first run of `retest()`, no `@test` is run, and on the second one, it fails because `x` is not defined at global scope.

The alternative is to turn `test_iseven` into a macro and declare it with `@testset_macro`:

```julia
using ReTest

macro test_iseven(x)
    quote
        @testset "iseven $($x)" begin
            @test iseven($x)
        end
    end
end

@testset_macro @test_iseven

@testset "test $x" for x=2:2:4
    @test_iseven(x)
end
```

Then, running `retest("iseven", verbose=2)` gives:

```
                    Pass
test 2          |      1
  iseven 2      |      1
test 4          |      1
  iseven 4      |      1
Main            |      2
```
