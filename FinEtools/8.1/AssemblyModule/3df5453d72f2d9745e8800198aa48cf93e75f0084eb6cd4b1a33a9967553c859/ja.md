```
startassembly!(self::SysmatAssemblerSparseDiag{T},
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
    row_nalldofs::IT,
    col_nalldofs::IT;
    force_init = false
    ) where {T, IT<:Integer}
```

対称正方行列の対角行列の組み立てを開始します。

このメソッドは行列の組み立てのためのバッファを作成します。最初の`assemble!`メソッドの呼び出しの前に呼び出す必要があります。

# 引数

  * `elem_mat_nrows` = 要素行列の行の次元;
  * `elem_mat_ncols` = 要素行列の列の次元;
  * `n_elem_mats` = 要素行列の数;
  * `row_nalldofs`= タプルとしての行の合計数;
  * `col_nalldofs`= タプルとしての列の合計数。

バッファに格納される値は最初は未定義です！

# 戻り値

  * `self`: 修正されたアセンブラ。
