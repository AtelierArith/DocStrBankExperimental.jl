```
cidfrm(cent)
```

フレームセンターに関連付けるためのフレームIDコードと名前を取得します。

### 引数

  * `cent`: 優先参照フレームがあるオブジェクトのIDコード

### 出力

フレームが見つからなかった場合は `nothing` を返すか、

  * `frcode`: `cent` に関連付けられたフレームのIDコード
  * `frname`: ID `frcode` のフレームの名前

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/cidfrm_c.html)
