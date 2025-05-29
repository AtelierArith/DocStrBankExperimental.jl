```
startassembly!(self::SysmatAssemblerSparseHRZLumpingSymm{T},
        elem_mat_nrows::IT,
        elem_mat_ncols::IT,
        n_elem_mats::IT,
        row_nalldofs::IT,
        col_nalldofs::IT;
        force_init = false
        ) where {T, IT<:Integer}
```

対称的にラプスされた対角の正方形グローバル行列のアセンブリを開始します。

このメソッドは、行列アセンブリのためのバッファを作成します。`assemble!`メソッドへの最初の呼び出しの前に呼び出す必要があります。

# 引数

  * `elem_mat_nrows` = 要素行列の行の次元;
  * `elem_mat_ncols` = 要素行列の列の次元;
  * `n_elem_mats` = 要素行列の数;
  * `row_nalldofs`= タプルとしての行の総数;
  * `col_nalldofs`= タプルとしての列の総数。

バッファに格納される値は最初は未定義です!

# 戻り値

  * `self`: 修正されたアセンブラ。
