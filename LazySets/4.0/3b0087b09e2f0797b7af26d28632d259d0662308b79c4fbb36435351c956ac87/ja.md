```
remove_redundant_constraints!(P::AbstractHPolygon)
```

制約表現における多角形のすべての冗長制約を削除します。

### 入力

  * `P` – 制約表現における多角形

### 出力

冗長制約がすべて削除された同じ多角形。

### 注意事項

有界多角形のみを考慮するため、多角形が有界であるためには少なくとも3つの制約が必要であり、残りの制約が3つ以下になると冗長制約の削除を停止します。したがって、無限大の多角形の場合、結果は予期しないものになる可能性があります。

### アルゴリズム

すべての連続する3つの制約の組を通過し、中央の制約が冗長であるかどうかを確認します。このため、制約がソートされていると仮定します。
