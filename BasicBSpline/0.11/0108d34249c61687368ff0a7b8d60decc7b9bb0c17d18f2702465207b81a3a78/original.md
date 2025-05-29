Construct uniform knot vector from given range.

$$
k=(k_1,\dots,k_l)
$$

# Examples

```jldoctest
julia> k = UniformKnotVector(1:8)
UniformKnotVector(1:8)

julia> UniformKnotVector(8:-1:3)
UniformKnotVector(3:1:8)
```
