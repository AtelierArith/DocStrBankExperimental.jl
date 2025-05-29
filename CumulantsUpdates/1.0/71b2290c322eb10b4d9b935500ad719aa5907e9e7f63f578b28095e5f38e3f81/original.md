norm(bt::SymmetricTensor{T, m}, p::Union{Float64, Int}=2) where {T<:AbstractFloat, m}

Returns Float, a p-norm of bt, supported for p ≠ 0

```jldoctest

julia> te = [-0.112639 0.124715 0.124715 0.268717 0.124715 0.268717 0.268717 0.046154];

julia> st = convert(SymmetricTensor, (reshape(te, (2,2,2))));

julia> norm(st)
0.5273572868359742

julia> norm(st, 2.5)
0.4468668679541424

julia> norm(st, 1)
1.339089
```
