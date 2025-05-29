```
nonsym(nbOne::Ti, size::Ti, diag_l::Ti, diag_u::Ti, spectrum::AbstractVector{Tv}) where {Tv<:Complex, Ti<:Integer}
```

デフォルトのニルポテント行列と行列のデフォルト初期化を使用して、非対称行列を生成します。

`nonsym`の使用法は`nonherm`のそれと同じです。詳細についてはその部分を参照してください。

与えられたスペクトルベクトルと行列の初期化の制約を考慮してください。詳細については[こちら](getting_started.md)をクリックしてください。
