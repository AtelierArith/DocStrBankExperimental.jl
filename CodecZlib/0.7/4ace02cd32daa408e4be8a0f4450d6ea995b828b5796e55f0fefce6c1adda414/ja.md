```
ZlibCompressor(;level=-1, windowbits=15)
```

zlib圧縮コーデックを作成します。

## 引数

  * `level` (-1..9): 圧縮レベル。1は最高の速度を提供し、9は最高の圧縮を提供し、0は全く圧縮を行わず（入力データはブロックごとに単純にコピーされます）。-1は速度と圧縮の間のデフォルトの妥協を要求します（現在はレベル6に相当します）。
  * `windowbits` (9..15): 履歴バッファのサイズは `2^windowbits` です。

!!! warning
    `serialize` と `deepcopy` は、このコーデックでは保存された生ポインタのために機能しません。

