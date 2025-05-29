```
find_queries(mol::MolGraph, query_diagram; subsets=[], filtering=true
    ) -> DictDiGraph, vprops, eprops
```

与えられた分子によってクエリ関係図を見つけます。フィルタリングされた図は、分子が持つクエリ関係を表します。
