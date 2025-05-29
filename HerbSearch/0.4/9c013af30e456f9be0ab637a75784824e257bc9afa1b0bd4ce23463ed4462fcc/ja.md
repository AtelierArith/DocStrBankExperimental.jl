```
derivation_heuristic(iter::MLFSIterator, domain::Vector{Int})
```

`MLFSIterator`のイテレータ型に対して`derivation_heuristic`を定義します。文法ルールであるドメイン内のインデックスを、対数確率が減少するようにソートします。

これにより、確率が等しい場合は列挙順序が反転します。
