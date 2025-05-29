```
partial_transpose(ρ::MPO, subsystem::Vector{Int})
```

指定された `subsystem` に対してMPOの部分転置を計算します。

MPO内の各サイトインデックスについて：

  * インデックスが `subsystem` に含まれている場合、テンソルは `swapind` を使用して未プライムインデックスとプライムインデックスを入れ替えることによって転置されます。
  * それ以外の場合、テンソルは変更されず（型の一貫性のために1.0で乗算されます）。

# 引数

  * `ρ::MPO`: 密度行列を表す行列積演算子。
  * `subsystem::Vector{Int}`: 転置を適用するサイトインデックスのベクトル（1ベース）。

# 戻り値

`subsystem` のサイトに対応するテンソルが部分転置されたMPO。

# 例

```julia
ρT = partial_transpose(ρ, [2, 3])
```
