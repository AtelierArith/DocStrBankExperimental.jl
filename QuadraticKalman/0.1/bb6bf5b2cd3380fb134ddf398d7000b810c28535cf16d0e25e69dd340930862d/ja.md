```
QKData(Y::AbstractArray{T,N}) where {T<:Real, N}
```

配列 `Y` から `QKData{T,N}` を構築します。

# 引数

  * `Y::AbstractArray{T,N}`: 入力配列（ベクトルまたは行列）

# 戻り値

  * `QKData{T,N}`: 検証されたデータ構造

# 説明

ベクトル入力の場合 (N=1):

  * M は 1 に設定されます
  * T_bar は length(Y) - 1 です

行列入力の場合 (N=2):

  * M は最初の次元のサイズです
  * T_bar は第二の次元のサイズから 1 を引いたものです
