```
selinv(A::SparseMatrixCSC; depermute=false)
    -> @NamedTuple{Z::AbstractMatrix, p::Vector{Int64}}
```

行列 `A` の選択逆行列 `Z` を計算します。`Z` のスパースパターンは `A` のコレスキー因子のそれに対応し、`Z` の非ゼロエントリは `A⁻¹` の対応するエントリと一致します。

# 引数

  * `A::SparseMatrixCSC`: 選択逆行列が計算されるスパース対称正定値行列。

# キーワード引数

  * `depermute::Bool`: 選択逆行列をデパーミュートするかどうか。

# 戻り値

名前付きタプル `Zp`。`Zp.Z` は選択逆行列で、`Zp.p` は対応するスパースコレスキー因子分解の置換ベクトルです。
