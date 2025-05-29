```
max_matching(G::SimpleGraph; method=:Blossom) -> Set{Int}
```

エドモンズのブロッサムアルゴリズムによって最大カーディナリティマッチングを計算し、一致したエッジのセットを返します。
