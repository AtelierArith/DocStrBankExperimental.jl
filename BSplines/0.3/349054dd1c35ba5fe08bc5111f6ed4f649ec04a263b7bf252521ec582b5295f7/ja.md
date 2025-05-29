```
basismatrix(basis::BSplineBasis, xvalues; indices=eachindex(basis))
```

行列 `[basis[i](x) for x=xvalues, i=indices]` を計算します。

# 例

```jldoctest
julia> basis = BSplineBasis(3, 0:5);

julia> x = [0.3, 1.5, 3.2, 4.5];

julia> basismatrix(basis, x)
4×7 Matrix{Float64}:
 0.49  0.465  0.045  0.0    0.0    0.0    0.0
 0.0   0.125  0.75   0.125  0.0    0.0    0.0
 0.0   0.0    0.0    0.32   0.66   0.02   0.0
 0.0   0.0    0.0    0.0    0.125  0.625  0.25
```
