```
matrix_repr(xi::SkewDiagram)
```

ダイアグラム `xi` のスパース表現を返します。すなわち、`A` というスパース配列で、`A[i,j] == 1` であるのは、`(i,j)` が `xi.lam` に含まれているが `xi.mu` には含まれていない場合です。
