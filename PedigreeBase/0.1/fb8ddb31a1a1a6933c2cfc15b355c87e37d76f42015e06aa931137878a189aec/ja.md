```
Ainv = get_mgsnrminv(mgslist; rank=0)
```

母数（加法）関係行列の逆行列を、父系および母方祖父（MGS）を持つ系図リスト `mgslist` から「ヘンダーソンの」方法を使用して計算します。近親交配は無視されます。詳細については、Henderson (1975) を参照してください。出力は Float64 の SparseMatrixCSC であり、一時的な行列として SparseMatrixDict（すなわちハッシュ行列）が使用されます。Aの逆行列のサイズを固定したい場合は、`rank` を指定してください。この関数は、より大きなサイズ `rank` または系図内の最大IDを持つ逆行列を作成します。
