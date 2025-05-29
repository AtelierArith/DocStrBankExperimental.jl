```
Random.rand(M::FixedRankMatrices; vector_at=nothing, kwargs...)
```

`vector_at`が`nothing`の場合、[`FixedRankMatrices`](@ref)多様体上のランダムな点を返します。直交行列は[`Stiefel`](@ref)多様体からサンプリングされ、特異値は一様にランダムにサンプリングされます。

`vector_at`が`nothing`でない場合、`FixedRankMatrices`多様体`M`上の点`vector_at`の接空間内でランダムな接ベクトルを生成します。
