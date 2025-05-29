```
eigenvalues_with_multiplicities(R::QQBarField, A::ZZMatrix)
eigenvalues_with_multiplicities(R::QQBarField, A::QQMatrix)
```

代数数の体 `R` における行列 `A` の固有値を、その代数的重複度と共にタプルのベクトルとして返します。出力配列は代数数のデフォルトのソート順でソートされています。
