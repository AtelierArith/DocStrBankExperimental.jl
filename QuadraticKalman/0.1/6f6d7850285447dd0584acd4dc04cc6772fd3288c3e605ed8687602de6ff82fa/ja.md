```
get_measurement(data::QKData{T,N}, t::Int) where {T<:Real, N}
```

QKDataから時刻tの測定値を抽出します。ベクトルデータの場合はスカラーを返し、行列データの場合はベクトルを返します。

# 引数

  * `data::QKData{T,N}`: データ構造
  * `t::Int`: 時間インデックス（1ベース）

# 戻り値

  * N=1の場合: 単一の測定値 Y[t]
  * N=2の場合: 測定値のベクトル Y[:,t]

# 例外

  * tが範囲外の場合はArgumentErrorをスローします。
