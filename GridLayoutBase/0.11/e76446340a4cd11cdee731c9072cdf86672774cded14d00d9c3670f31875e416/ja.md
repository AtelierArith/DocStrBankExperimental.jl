```
GridLayout(g::Union{GridPosition, GridSubposition}, args...; kwargs...)
```

親の `GridLayout` の位置 `g` に `GridLayout` を作成します。`g` が `GridPosition` の場合は親の `GridLayout` に、`GridSubposition` の場合はネストされた子の `GridLayout` に作成されます。`args` と `kwargs` は通常の `GridLayout` コンストラクタに渡されます。
