```
gcpool(name; start=1, room=100, lenout=128)
```

カーネルプールからカーネル変数の値を返します。

### 引数

  * `name`: 値を返す変数の名前
  * `start`: 名前の取得を開始するコンポーネント (デフォルト: 1)
  * `room`: 返す最大値の数 (デフォルト: 100)
  * `lenout`: 返す最長文字列の長さ (デフォルト: 128)

### 出力

変数が存在する場合は値の配列を返し、存在しない場合は `nothing` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gcpool_c.html)
