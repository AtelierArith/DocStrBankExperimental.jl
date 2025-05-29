```
overwrite(z)(a, b)
```

`overwrite(z)` is a function which returns `b` always. `lhs[] := rhs` is equivalent to `lhs[] <<overwrite>>= rhs`.

```jldoctest setup=:(using Finch)
julia> a = Tensor(SparseList(Element(0.0)), [0, 1.1, 0, 4.4, 0])
5 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 0.0
 1.1
 0.0
 4.4
 0.0

julia> x = Scalar(0.0); @finch for i=_; x[] <<overwrite>>= a[i] end;

julia> x[]
0.0
```
