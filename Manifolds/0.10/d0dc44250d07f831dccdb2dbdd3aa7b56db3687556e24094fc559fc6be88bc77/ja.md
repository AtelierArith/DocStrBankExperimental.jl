```
Random.rand(M::HeisenbergMatrices; vector_at = nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、平均0、標準偏差`σ`の正規分布から最初の行と最後の列の要素をサンプリングすることによって、[`HeisenbergMatrices`](@ref) `M`上のランダムな点を返します。

`vector_at`が`nothing`でない場合、平均0、標準偏差`σ`の正規分布を使用して、[`HeisenbergMatrices`](@ref)上の点`vector_at`の接空間からランダムな接ベクトルを返します。
