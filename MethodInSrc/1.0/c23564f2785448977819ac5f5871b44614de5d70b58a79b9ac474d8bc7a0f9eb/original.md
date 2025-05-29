```
@isinsrc f([x, y,...])
```

Return true if the method that would be called for the expression is in the source directory ("src") of the module in which the test running.

`@isinsrc` is meant to be called from within a module's "test" directory. The src directory is then found via "test/../src".

### Example

Verify that the method for `sum` is defined in `MyPackage`.

```julia
using MyPackage
using MethodInSrc
using Test

m = MyPackage.AMatrix(3)
@test @isinsrc sum(m)
```
