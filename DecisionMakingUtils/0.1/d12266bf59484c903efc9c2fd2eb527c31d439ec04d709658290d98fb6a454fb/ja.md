```
FourierBasisBuffer(ϕ::FourierBasis)
```

フォーリエ基底のための事前割り当てバッファを作成し、基底の呼び出しごとに割り当てを避けるために使用します。

参照: [`FourierBasis`](@ref)

# 例

```jldoctest julia> f = FourierBasis(2, 1, 2);

julia> buff = FourierBasisBuffer(f);

julia> x = [0.0, 0.5];

julia> feats = f(buff, x) 6-element Array{Float64,1}:   1.0   6.123233995736766e-17   1.0   6.123233995736766e-17   1.0  -1.0
```
