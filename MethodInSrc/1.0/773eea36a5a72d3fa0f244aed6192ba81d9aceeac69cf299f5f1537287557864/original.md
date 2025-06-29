```
module MethodInSrc
```

`MethodInSrc` provides tools to use in your test suite that verify that a function call dispatches (or does not) to a method defined in your module. They are meant to verify that a specialized method is called rather than a more generic one. (Or vice versa.)

This module exports `@isinsrc`, `@insrc`, `@ninsrc`, `@isinmodule`, `@inmodule`, and  `@ninmodule`.

`@isinsrc f(x)` returns `true` if the method for `f(x)` is found under `../src`. But, it does not evaluate `f(x)`.

`@insrc f(x)` throws an error if the method for `f(x)` is not found under `../src`. Otherwise, it evaluates `f(x)`.

`@ninsrc` is the same as `@insrc` except that it throws if the method *is* under `../src`.

The first three macros are meant to be used in files in your module's "test" directory. In this case, `@isinsrc f([x,...])` returns `true` if the method that would be called by `f([x,...])` was defined in the module's "src" directory.

See the doc strings for `@isinmodule`, `@inmodule`, and  `@ninmodule`.

## Examples

Suppose the type `MyPackage.AMatrix` represents a square matrix whose elements are all equal to `1`. `MyPackage` extends `Base.sum` with an efficient method for `::AMatrix`. `MyPackage` also includes an efficient function `prod(::AMatrix)`. But, we neglected to write `Base.prod` or `import Base: prod`. So `MyPackage.prod` is not an extension of `Base.prod`.

### `@isinsrc`

Use `@isinsrc` to check that both `sum` and `prod` extend `Base` functions. (`prod` does not!)

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix{Int}(3)
@test @isinsrc sum(m)
@test @isinsrc prod(m)  # This will fail!
```

### `@insrc`, `@ninsrc`

Use `@insrc` if you are too lazy to write two tests, one to verify that you have the correct method, and another to test its correctness.

`@insrc` verifies that the methods are defined in "../src", and then evaluate the expressions. Here, it is assumed we know that `MyPackage.prod` is a different function and test for it. These tests all pass.

```julia
using MyPackage
using MethodInSrc
using Test

N = 3
m = MyPackage.AMatrix{Int}(N)

# Note that `@insrc` takes the next expression as an argument.
# We need to test just the function call.
@test_throws ErrorException 1 == @insrc prod(m)   # This finds the method.
@test_throws ErrorException @insrc(prod(m)) == 1  # This does too.
@test 1 == @ninsrc prod(m)  # Do the test if the method is generic

# The following methods are found in "../src", so the expressions are evaluated
@test N^2 == @insrc sum(m)
@test (@insrc sum(m)) == N^2
@test @insrc(MyPackage.prod(m)) == 1
```
