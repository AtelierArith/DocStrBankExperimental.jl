```
automaton_constructor(Σ::AbstractVector{<:AbstractMatrix})
```

状態間の許容遷移を追跡するオートマトンを生成します。`Σ` は TAR モデルに対応する行列のベクトルであり、[`perms`](@ref) によって生成されたデフォルトの順序を仮定しています。

```
automaton_constructor(Σ::AbstractVector{<:AbstractMatrix}, seqlist)
```

カスタムのレジームシーケンスのリストを考慮して、状態間の許容遷移を追跡するオートマトンを生成します。
