空の `PairwiseListMatrix` は、指定された `Type` と要素数 `nelements` に対して作成できます。`diagonal`（デフォルトは `false`）を `true` に設定すると、リストが対角要素のためのスペースを必要とすることを示します。`diagonal` が `false` の場合、対角値はリストではなく `diag` フィールドのベクターに格納されます。`diag` ベクターは、オプションの `diagonalvalue` 引数（デフォルトは `0`）で埋めることができます。

```julia
PairwiseListMatrix(Int, 3)
PairwiseListMatrix(Int, 3, true)
```
