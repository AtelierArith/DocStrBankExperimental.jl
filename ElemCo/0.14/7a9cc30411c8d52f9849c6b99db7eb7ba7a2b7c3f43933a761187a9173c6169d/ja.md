```
@write_ints(file="FCIDUMP", tol=-1.0)
```

ファイル `file` にFCIDump積分を出力します。

`tol` が負の場合、すべての積分が書き込まれます。それ以外の場合は、絶対値が `tol` より大きい積分のみが書き込まれます。
