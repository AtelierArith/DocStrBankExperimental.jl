```
AffineExpression{T}
```

Data structure to represent affine expressions, such as $x+2y+z+4$.

### Examples

```jldoctest
julia> @affinevars x y z
3-element Vector{AffineExpression{Int64}}:
 x
 y
 z

julia> p1 = x + 2y + z + 4
x+2y+z+4
```
