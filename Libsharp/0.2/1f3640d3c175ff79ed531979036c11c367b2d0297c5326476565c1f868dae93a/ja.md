```
make_alm_info(lmax::Integer, mmax::Integer, stride::Integer, 
    mstart::AbstractArray{T}) where T <: Integer
```

一般的な a_lm データ構造を初期化します。

# 引数

  * `lmax::Integer`: 最大球面調和 ℓ
  * `mmax::Integer`: 最大球面調和 m
  * `stride::Integer`: リング内の連続するピクセル間のストライド
  * `mstart::AbstractArray{T}`: 量子数 0, m を持つ係数のインデックス。mmax+1 のエントリを持つ必要があります。

# 戻り値

  * AlmInfo オブジェクト
