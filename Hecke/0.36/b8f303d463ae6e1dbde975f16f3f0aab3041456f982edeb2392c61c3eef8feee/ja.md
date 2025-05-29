```
completion(K::AbsSimpleNumField, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, precision::Int)
                                                -> LocalField, CompletionMap
```

$$
K
$$

の完備化は、$P$における評価によって誘導される位相に関して、非分岐p-進体のエイゼンシュタイン拡張として提示されます。

$$
K
$$

を完備化に埋め込むマップは、リフトを得るための点ごとの前像を許容します。このデータによってマップは一意に定義されないことに注意してください：$K$は$\deg P$個の埋め込みを持ちます。

このマップは、少なくとも`preciscion`の相対精度を保証します。
