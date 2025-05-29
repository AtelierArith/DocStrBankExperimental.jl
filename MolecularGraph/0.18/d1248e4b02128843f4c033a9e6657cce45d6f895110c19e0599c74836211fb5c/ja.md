```
modularproduct(g::SimpleGraph{T}, h::SimpleGraph{T};
    vmatch=(g1,h1)->true,
    edgefilter=(g1,g2,h1,h2)->has_edge(g,g1,g2)==has_edge(g,h1,h2)) where T
```

グラフ `g` と `h` のモジュラー積 `m` を返し、エッジが接続されているかどうかのマッピングを返します。ノード `g` と `h` を `m` のノードにマッピングするのは f(i, j) = (i - 1) * nv(h) + j であり、逆マッピングは f(i) = (div(i - 1, nv(h)) + 1, mod(i - 1, nv(h))) + 1 です。ここで、i は `g` のノード、j は `h` のノードです。
