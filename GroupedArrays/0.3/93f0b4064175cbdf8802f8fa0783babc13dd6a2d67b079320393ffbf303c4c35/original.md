```
GroupedArray(args... [; coalesce = false, sort = true])
```

Construct a `GroupedArray` taking on distinct values for the groups formed by elements of `args`

### Arguments

  * `args...`: `AbstractArrays` of same sizes.

### Keyword arguments

  * `coalesce::Bool`: should missing values considered as distinct grotups indicators?
  * `sort::Union{Bool, Nothing}`: should the order of the groups be the sort order? Set to `nothing` for best performance.

### Examples

```julia
using GroupedArrays
p1 = ["a", "a", "b", "b", missing, missing]
GroupedArray(p1)
GroupedArray(p1; coalesce = true)
p2 = [1, 1, 1, 2, 2, 2]
GroupedArray(p1, p2)
```
