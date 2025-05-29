```
(xg, yg, ...) = ndgrid(v1, v2, ...)
```

Construct `ndgrid` tuple for `AbstractVector` inputs. Each output has a lazy grid type (subtype of `AbstractGrid`) according to the corresponding input vector type.

# Examples

```jldoctest
julia> xg, yg = ndgrid(1:3, [:a, :b])
([1 1; 2 2; 3 3], [:a :b; :a :b; :a :b])

julia> xg
3×2 LazyGrids.GridUR{Int64, 1, 2}:
 1  1
 2  2
 3  3

julia> yg
3×2 LazyGrids.GridAV{Symbol, 2, 2}:
 :a  :b
 :a  :b
 :a  :b
```
