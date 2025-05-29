```
filterop(z)(cond, arg)
```

`filterop(z)` is a function which returns `ifelse(cond, arg, z)`. This operation is handy for filtering out values based on a mask or a predicate. `map(filterop(0), cond, arg)` is analogous to `filter(x -> cond ? x: z, arg)`.

```jldoctest setup=:(using Finch)
julia> a = Tensor(SparseList(Element(0.0)), [0, 1.1, 0, 4.4, 0])
5 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 0.0
 1.1
 0.0
 4.4
 0.0

julia> x = Tensor(SparseList(Element(0.0)));

julia> c = Tensor(SparseList(Element(false)), [false, false, false, true, false]);

julia> @finch (x .= 0; for i=_; x[i] = filterop(0)(c[i], a[i]) end)
(x = Tensor(SparseList{Int64}(Element{0.0, Float64, Int64}([4.4]), 5, [1, 2], [4])),)

julia> x
5 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 0.0
 0.0
 0.0
 4.4
 0.0
```
