```julia
sortDFG(vars; by, kwargs...)

```

`Base.sort`の便利なラッパーです。変数（因子）リストを意味のある方法でソートします（`timestamp`、`label`などによって）、例えば`[:april;:x1_3;:x1_6;]`です。変数と因子はデフォルトでtimestampによってソートされ、Symbolsには`natural_lt`が使用されます。詳細についてはBase.sortを参照してください。

ノート

  * 完璧ではありませんが、ネイティブソートよりは良い結果を出します。

例

`sortDFG(ls(dfg))` `sortDFG(ls(dfg), by=getLabel, lt=natural_lt)`

関連

ls, lsf
