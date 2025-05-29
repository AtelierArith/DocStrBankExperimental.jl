`idx_max([T=Float64], size::NTuple{N, Int};         offset=CtrFT,         dims=ntuple(+, N),         scale=ScaUnit,         weight=1,         accumulator=sum)`

は、オフセットとスケーリングが適用された後のすべてのインデックス次元の絶対値の最大値を返します。比較演算と組み合わせることで、ボックス状のアパーチャを簡単に得ることができます。詳細は以下を参照してください。すべてのオプションの説明については `rr2` を参照してください。

```jldoctest
julia> idx_max((5,5)) .< 2
5×5 BitMatrix:
 0  0  0  0  0
 0  1  1  1  0
 0  1  1  1  0
 0  1  1  1  0
 0  0  0  0  0
```

---

```
idx_max(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは `idx_max(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
