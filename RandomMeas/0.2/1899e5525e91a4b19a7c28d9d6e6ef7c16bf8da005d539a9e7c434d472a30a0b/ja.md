```
reduce_to_subsystem(ψ::MPS, subsystem::Vector{Int64})
```

指定されたサブシステムに対して、MPS `ψ` で表される純粋状態の縮約密度行列を計算します。

この関数は、まず `ψ` の外積を取ることで密度行列を構築し、その後 `reduce_to_subsystem` のMPOバージョンを適用して、`subsystem` で指定されたサイトの縮約密度行列を取得します。

# 引数

  * `ψ::MPS`: 純粋量子状態を表す行列積状態。
  * `subsystem::Vector{Int64}`: サブシステムを保持するために指定されたサイトインデックスのベクトル（1ベース）。

# 戻り値

指定されたサブシステムに対する縮約密度行列を表すMPO。

# 例

```julia
ρ_sub = reduce_to_subsystem(ψ, [2, 3])
```
