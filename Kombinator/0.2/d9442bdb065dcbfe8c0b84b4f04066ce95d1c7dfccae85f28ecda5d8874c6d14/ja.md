```
abstract type MultipleMinBudgetedSolution
```

複数の解が利用可能なときの `MinBudgetedSolution` のタイプで、組合せインスタンスによって指定された予算の複数の値（通常はゼロから最大値まで）を持ちます。

このタイプのオブジェクトは、`CombinatorialSolution` の通常のフィールドを実装する必要がありますが、`solutions` も実装する必要があります。これは、予算値から対応する解へのマッピングです（`solutions`[i]`は`i`の最小予算に対応します）。
