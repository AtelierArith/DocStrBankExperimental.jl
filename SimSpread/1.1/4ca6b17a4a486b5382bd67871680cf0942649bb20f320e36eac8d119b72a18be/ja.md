```
Base.split(y::NamedArray, k::Int64; seed::Int64=1)
```

`y`のソースノードを交差検証のために`k`グループに分割します。

# 引数

  * `y::AbstractMatrix`: 薬剤-ターゲットの長方形隣接行列。
  * `k::Int64`: データ分割に使用するグループの数。
  * `seed::Int64`: データ分割に使用されるシード。
