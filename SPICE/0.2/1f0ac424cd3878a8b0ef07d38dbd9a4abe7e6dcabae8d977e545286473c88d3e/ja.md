```
frinfo(frcode)
```

フレームの変換に必要な最小限の属性を取得します。

### 引数

  * `frcode`: 参照フレームのIDコード

### 出力

  * `cent`: フレームの中心
  * `frclss`: フレームのクラス（タイプ）
  * `clssid`: そのクラス内のフレームのIDコード

ID `frcode` のフレームが見つからない場合は `nothing` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/frinfo_c.html)
