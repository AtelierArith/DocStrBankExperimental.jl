```julia
simplify(x; expand=false,
            threaded=false,
            thread_subtree_cutoff=100,
            rewriter=nothing)
```

式 (`x`) を `rewriter` を適用して変更がなくなるまで簡略化します。`expand=true` は各フィックスポイント反復の最初に [`expand`](/api/#expand) を適用します。

デフォルトでは、simplify は分母がゼロでないと仮定し、分数の約分を許可します。これを防ぐには `simplify_fractions=false` を渡してください。
