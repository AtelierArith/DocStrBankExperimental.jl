`idx_min([T=Float64], size::NTuple{N, Int};         offset=CtrFT,         dims=ntuple(+, N),         scale=ScaUnit,         weight=1,         accumulator=sum)`

は、オフセットとスケーリングが適用された後のすべてのインデックス次元の絶対値の最小値を返します。比較演算と組み合わせることで、十字型のアパーチャを簡単に得ることができます。詳細は以下を参照してください。すべてのオプションの説明については `rr2` を参照してください。

```jldoctest
julia> idx_min((5,5)) .< 1
5×5 BitMatrix:
 0  0  1  0  0
 0  0  1  0  0
 1  1  1  1  1
 0  0  1  0  0
 0  0  1  0  0
```

---

```
idx_min(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは `idx_min(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
