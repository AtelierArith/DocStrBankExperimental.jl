```
get_wigner_array(w::AbstractWigner{T}) where {T}
```

オフセット配列を取得するためのユーティリティ関数で、インデックスは jₘᵢₙ から jₘₐₓ までです。

# 引数

  * `w::AbstractWigner{T}`: 量子数を含み、シンボルの種類に基づいてディスパッチします。

# 戻り値

  * `OffsetArray{T}`: ウィグナーシンボル用の配列です。
