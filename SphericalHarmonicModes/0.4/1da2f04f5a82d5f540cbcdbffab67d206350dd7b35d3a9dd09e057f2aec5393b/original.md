```
L2L1Triangle(l1_min::Int, l1_max::Int, Δl_max::Int, l2_min::Int = max(0, l1_min - Δl_max), l2_max = l1_max + Δl_max)
L2L1Triangle(l1_range::AbstractUnitRange{Int}, Δl_max::Int, l2_range::AbstractUnitRange{Int})
```

Return an iterator that loops over pairs of `(l2,l1)` where `l1` lies in `l1_range`, `l2` lies in `l2_range`, and `l2` and `l1` obey the triangle condition `max(0, l1 - Δl_max) ⩽ l2 ⩽ l1 + Δl_max`. If `l2_range` is not specified, it defaults to the maximal range permissible.

!!! warning
    The ranges `l1_range` and `l2_range` will be curtailed to the minimal permissible subsets.


# Examples

```jldoctest
julia> L2L1Triangle(1:2, 2) |> collect
9-element Vector{Tuple{Int64, Int64}}:
 (0, 1)
 (1, 1)
 (2, 1)
 (3, 1)
 (0, 2)
 (1, 2)
 (2, 2)
 (3, 2)
 (4, 2)

julia> L2L1Triangle(2:3, 1) |> collect
6-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 2)
 (3, 2)
 (2, 3)
 (3, 3)
 (4, 3)

julia> L2L1Triangle(2:3, 1, 2:3) |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 2)
 (2, 3)
 (3, 3)
```
