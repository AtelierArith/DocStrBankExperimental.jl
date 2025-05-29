```
integer_genera(sig_pair::Vector{Int}, determinant::RationalUnion;
       min_scale::RationalUnion = min(one(QQ), QQ(abs(determinant))),
       max_scale::RationalUnion = max(one(QQ), QQ(abs(determinant))),
       even=false)                                         -> Vector{ZZGenus}
```

与えられた条件を満たすすべての属のリストを返します。非整数の $\mathbb Z$-格子の属もサポートされています。

# 引数

  * `sig_pair`: シグネチャを与える非負整数のペア
  * `determinant`: 有理数; 符号は無視されます
  * `min_scale`: 有理数; `min_scale` の整数倍である属のみを返します（デフォルト: `min(one(QQ), QQ(abs(determinant)))`）
  * `max_scale`: 有理数; `max_scale` がスケールの整数倍である属のみを返します（デフォルト: `max(one(QQ), QQ(abs(determinant)))`）
  * `even`: ブール値; true に設定されている場合、偶数の属のみを返します（デフォルト: `false`）
