```
choose(z)(a, b)
```

`choose(z)` is a function which returns whichever of `a` or `b` is not [isequal](https://docs.julialang.org/en/v1/base/base/#Base.isequal) to `z`. If neither are `z`, then return `a`. Useful for getting the first nonfill value in a sparse array.

```jldoctest setup=:(using Finch)
julia> a = Tensor(SparseList(Element(0.0)), [0, 1.1, 0, 4.4, 0])
5 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 0.0
 1.1
 0.0
 4.4
 0.0

julia> x = Scalar(0.0); @finch for i=_; x[] <<choose(0.0)>>= a[i] end;

julia> x[]
1.1
```
