```
dummy(y)
```

Compute dummy table from a categorical variable.

  * `y` : A categorical variable.

The output `Y` (dummy table) is a BitMatrix.

## Examples

```julia
using Jchemo

y = ["d", "a", "b", "c", "b", "c"]
#y =  rand(1:3, 7)
res = dummy(y)
@names res
res.Y
```
