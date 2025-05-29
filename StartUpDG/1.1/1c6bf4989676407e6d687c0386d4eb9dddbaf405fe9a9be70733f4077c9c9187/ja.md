```
RefElemData(elem::Union{Line, Quad, Hex}, approximation_type::Polynomial{Gauss}, N)
```

各次元において(N+1)点のガウス積分を用いて`rd::RefElemData`を構築します。
