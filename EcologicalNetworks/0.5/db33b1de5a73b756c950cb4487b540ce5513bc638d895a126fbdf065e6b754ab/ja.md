```
centrality_harmonic(N::UnipartiteNetwork; nmax::Int64=20)
```

この関数は内部で `shortest_path` を呼び出します - `nmax` 引数は試行される最大パス長です。
