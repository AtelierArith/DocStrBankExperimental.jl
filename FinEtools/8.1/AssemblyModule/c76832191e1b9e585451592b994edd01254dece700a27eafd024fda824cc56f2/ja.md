```
startassembly!(self::SysmatAssemblerSparse{T},
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
    row_nalldofs::IT,
    col_nalldofs::IT;
    force_init = false
    ) where {T, IT<:Integer}
```

グローバル行列のアセンブリを開始します。

このメソッドは行列アセンブリのためのバッファを作成します。最初の`assemble!`メソッドの呼び出しの前に呼び出す必要があります。

# 引数

  * `elem_mat_nrows` = 要素行列の行の次元;
  * `elem_mat_ncols` = 要素行列の列の次元;
  * `n_elem_mats` = 要素行列の数;
  * `row_nalldofs`= タプルとしての行の総数;
  * `col_nalldofs`= タプルとしての列の総数。

アセンブラの`buffer_pointer`フィールドが0の場合、つまりアセンブラが作成された後の状態では、入力の次元に応じてバッファが適切にサイズ変更されます。それ以外の場合、バッファは完全に変更されません。`buffer_pointer`はバッファの先頭、すなわち1に設定されます。

# 戻り値

  * `self`: 修正されたアセンブラ。

!!! note
    バッファは最初は何も意味のあるもので埋められていません。アセンブリの後、意味のある数値は`(self._buffer_pointer - 1)`のエントリのみです。注意してください！


!!! note
    より多くの数値がアセンブルされると、バッファは自動的にサイズ変更される場合があります。ただし、この操作は必ずしも効率的で迅速であるとは限りません。

