```
remove_redundant_constraints(constraints::AbstractVector{<:HalfSpace}; backend=nothing)
```

与えられた線形制約のリストから冗長な制約を削除します。

### 入力

  * `constraints` – 制約のリスト
  * `backend`     – （オプション、デフォルト: `nothing`）線形計画を解くために使用されるバックエンド

### 出力

冗長な制約が削除された制約のリスト、または制約が実現不可能な場合は空のリスト。

### 注意事項

`backend` が `nothing` の場合、`default_lp_solver(N)` にデフォルト設定されます。

### アルゴリズム

詳細については `[remove_redundant_constraints!(::AbstractVector{<:HalfSpace})](@ref)` を参照してください。
