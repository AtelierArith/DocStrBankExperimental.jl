dataupdat(X::Matrix{T}, Xplus::Matrix{T}) where T<:AbstractFloat

サイズ(X)のMatrix{Float}を返します。最初のu = size(Xup, 1)行のXが削除され、最後にupdat Xplusが追加されます。

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
