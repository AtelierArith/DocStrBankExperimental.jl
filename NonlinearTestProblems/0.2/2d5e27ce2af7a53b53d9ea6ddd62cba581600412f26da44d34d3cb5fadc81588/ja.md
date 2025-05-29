`root(problem)`

テスト問題の根（解）。形式的には、

```julia
problem(root(problem)) ≈ zeros(range_dimension(problem))
```

問題は一意の根を持つことが保証されています。
