```
selinv(F::SparseArrays.CHOLMOD.Factor; depermute=false)
    -> @NamedTuple{Z::AbstractMatrix, p::Vector{Int64}}
```

スパースコレスキー因子分解 `F` に基づいて、行列 `A` の選択逆行列 `Z` を計算します。

# 引数

  * `F::SparseArrays.CHOLMOD.Factor`:       行列 `A` のスパースコレスキー因子分解。       `F` は、`A` の選択逆行列の計算に内部的に使用されます。

# キーワード引数

  * `depermute::Bool`: 選択逆行列をデパーミュートするかどうか。

# 戻り値

名前付きタプル `Zp`。 `Zp.Z` は選択逆行列であり、`Zp.p` は対応するスパースコレスキー因子分解の置換ベクトルです。
