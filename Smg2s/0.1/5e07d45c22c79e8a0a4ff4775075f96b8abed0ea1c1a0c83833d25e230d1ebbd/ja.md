```
nonsym(size::Ti, diag_l::Ti, diag_u::Ti, spectrum::AbstractVector{Tv}, Am::SparseMatrixCSC{Tv2, Ti}, nilp::Nilpotent{Ti}) where {Tv<:Complex, Tv2<:Real, Ti<:Integer}
```

ユーザー提供のニルポテント行列と行列の初期化を使用して非対称行列を生成します。

`nonsym`の使用法は`nonherm`と同じですので、詳細についてはその部分を参照してください。

与えられたスペクトルベクトルと行列の初期化の制約を考慮してください。詳細については[こちら](getting_started.md)をクリックしてください。
