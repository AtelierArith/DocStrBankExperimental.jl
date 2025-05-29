```
remove_redundant_constraints(P::HPoly{N}; [backend]=nothing) where {N}
```

制約表現における多面体の冗長な制約を削除します。

### 入力

  * `P`       – 多面体
  * `backend` – （オプション、デフォルト: `nothing`）線形計画を解くために使用されるバックエンド

### 出力

冗長な制約がない `P` と同等の多面体、または `P` が空であると検出された場合は空集合。これは、制約が実現不可能な場合に発生する可能性があります。

### 注意事項

`backend` が `nothing` の場合、デフォルトで `default_lp_solver(N)` に設定されます。

### アルゴリズム

詳細については `remove_redundant_constraints!(::AbstractVector{<:HalfSpace})` を参照してください。
