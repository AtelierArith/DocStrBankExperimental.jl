```julia
simplify(x; expand=false,
            threaded=false,
            thread_subtree_cutoff=100,
            rewriter=nothing)
```

Simplify an expression (`x`) by applying `rewriter` until there are no changes. `expand=true` applies [`expand`](/api/#expand) in the beginning of each fixpoint iteration.

By default, simplify will assume denominators are not zero and allow cancellation in fractions. Pass `simplify_fractions=false` to prevent this.
