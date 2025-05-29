```
XPRSaddcols(prob, objcoef, mat, lb, ub)
```

`XPRSaddcols`の実装は、引数`ncols`、`ncoefs`、`start`、`rowind`、`rowcoef`を単一の引数`mat`に結合します。

`mat.colptr`および`mat.rowval`の値は1ベースのインデックスであると仮定されており（関数はCライブラリを呼び出すために暗黙的にそれらを0ベースのインデックスに変換します）。
