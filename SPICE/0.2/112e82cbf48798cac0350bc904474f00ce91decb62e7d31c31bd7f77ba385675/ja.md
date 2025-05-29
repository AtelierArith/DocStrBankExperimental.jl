```
dlafps(handle, descr)
```

指定されたセグメントの前にあるセグメントをDLAファイルで見つけます。

### 引数

  * `handle`: 開いているDLAファイルのハンドル
  * `descr`: DLAセグメントの記述子

### 出力

DLAファイル内の前のセグメントの記述子を返すか、見つからなかった場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dlafps_c.html)
