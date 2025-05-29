```
@insrc f([x, y,...])
```

Evaluate the expression if the method called is defined in the source directory ("src") of the module in which the test running. Otherwise, throw an `ErrorException`.

`@insrc` is meant to be called from within a module's "test" directory. The src directory is then found via "test/../src".

### Example

Verify that the method for `sum` is defined in `MyPackage`.

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix(3)
@test @insrc(sum(m)) == 9
```
