```
Optimisers.thaw!(tree)
```

[`freeze!`](@ref Optimisers.freeze!)の逆です。すべてのパラメータに適用され、すべての `Leaf(rule, state, frozen = true)` を `Leaf(rule, state, frozen = false)` に変異させます。
