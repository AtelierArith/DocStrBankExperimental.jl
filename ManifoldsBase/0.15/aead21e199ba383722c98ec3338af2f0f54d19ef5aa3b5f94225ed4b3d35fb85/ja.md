```
Random.rand(M::AbstractManifold, [d::Integer]; vector_at=nothing)
Random.rand(rng::AbstractRNG, M::AbstractManifold, [d::Integer]; vector_at=nothing)
```

多様体 `M` 上のランダムな点を生成します（`vector_at` が `nothing` の場合）または点 `vector_at` での接ベクトルを生成します（`nothing` でない場合）。

オプションで使用する乱数生成器 `rng` を指定できます。オプションの整数 `d` は、`d` 個の点または接ベクトルのベクトルを生成することを示します。

!!! note
    通常、コンパクトな多様体では一様分布が期待され、非コンパクトな多様体および接ベクトルではガウス様分布が期待されますが、保証されるものではありません。分布はリリース間で変わる可能性があります。

    特定の多様体に対する `rand` メソッドは、追加のキーワード引数を取る場合があります。

