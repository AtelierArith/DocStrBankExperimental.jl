dataupdat(X::Matrix{T}, Xplus::Matrix{T}) where T<:AbstractFloat

Returns Matrix{Float} of size(X), first u = size(Xup, 1) rows of X are removed and at the end the updat Xplus is appended.

```jldocstests

julia> a = ones(4,4);

julia> b = zeros(2,4);

julia> dataupdat(a,b)
4×4 Array{Float64,2}:
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

```
