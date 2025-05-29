```
centrality_closeness(N::UnipartiteNetwork; nmax::Int64=20)
```

この関数は内部で `shortest_path` を呼び出します – `nmax` 引数は試行される最大パス長です。

#### 参考文献

  * Bavelas, A., 1950. Communication Patterns in Task‐Oriented Groups. The Journal of the Acoustical Society of America 22, 725–730. doi:10.1121/1.1906679
