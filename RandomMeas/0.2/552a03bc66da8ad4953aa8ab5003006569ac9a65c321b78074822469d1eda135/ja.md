```
get_trace_moments(ψ::Union{MPS, MPO}, k_vector::Vector{Int}, subsystem::Vector{Int}=collect(1:length(ψ)))
```

指定されたサブシステムに対する量子状態 `ψ` のトレースモーメントのベクトルを計算します。

`k_vector` の各モーメント順序 `k` に対して、関数は `reduce_to_subsystem(ψ, subsystem)` を適用して得られた縮小密度行列の k 番目のトレースモーメントを計算します。

# 引数

  * `ψ::Union{MPS, MPO}`: MPS（純粋状態の場合）または MPO（混合状態の場合）として表される量子状態。
  * `k_vector::Vector{Int}`: トレースモーメントが計算される整数モーメント順序のベクトル（各々 ≥ 1）。
  * `subsystem::Vector{Int}`（オプション）: 考慮するサブシステムを指定するサイトインデックスのベクトル（1ベース）。デフォルトはすべてのサイト。

# 戻り値

`k_vector` のエントリに対応する k 番目のトレースモーメントであるスカラーのベクトル。

# 例

```julia
moments = get_trace_moments(ψ, [1, 2, 3], [1, 2, 3])
```
