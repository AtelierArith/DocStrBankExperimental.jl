```
Broadcasting(f)
```

Returns a mapping that represents the "broadcasted" version of the function `f`.

# Example

```jldoctest
using Gridap.Arrays

a = [3,2]
b = [2,1]

bm = Broadcasting(+)

c = evaluate(bm,a,b)

println(c)

# output
[5, 3]
```
