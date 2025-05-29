```
reduce_to_subsystem(ρ::MPO, subsystem::Vector{Int64})
```

指定されたサブシステムのための縮小密度行列（MPOとして）を計算します。

# 引数

  * `ρ::MPO`: 完全な密度行列を表す行列積演算子。
  * `subsystem::Vector{Int64}`: 保持するサブシステムを指定するサイトインデックスのベクトル（1ベース）。

# 戻り値

`subsystem`で指定されたサイトに対する縮小密度行列を表すMPO。

# 例

```julia
ρ_reduced = reduce_to_subsystem(ρ, [2, 3])
```
