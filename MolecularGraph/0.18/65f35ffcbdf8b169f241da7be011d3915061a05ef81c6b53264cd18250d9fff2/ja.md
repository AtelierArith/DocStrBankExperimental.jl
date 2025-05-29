```
to_triple_bond(mol::SimpleMolGraph) -> Nothing
```

分子を標準化して、すべての1,3-ジポール基が三重結合と単結合として表されるようにします（例：ジアゾ基 C=[N+]=[N-] -> [C-][N+]#N）。
