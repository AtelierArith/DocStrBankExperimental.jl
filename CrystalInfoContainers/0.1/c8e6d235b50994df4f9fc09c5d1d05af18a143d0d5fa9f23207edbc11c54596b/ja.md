get*key*datanames(d::LoopCategory; drop_same = false)

`d`のキーのデータ名をシンボルとして返します。`drop_same`がtrueの場合、複数の値を取ることができるキーのデータ名のみを返します。つまり、親データ名が複数の値を取る場合です。
