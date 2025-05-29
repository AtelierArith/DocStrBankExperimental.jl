```
dskobj!(set, dsk)
```

指定されたDSKファイルに提供されているすべてのオブジェクトのボディIDコードのセットを見つけます。

### 引数

  * `dsk`: DSKファイルの名前
  * `set`または`len`: 事前に割り当てられた`SpiceIntCell`または出力セットの`size`。

### 出力

DSKファイル内のオブジェクトのIDコードのセットを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskobj_c.html)
