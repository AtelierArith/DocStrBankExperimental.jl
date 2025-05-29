```
getfov(instid, room=10, shapelen=128, framelen=128)
```

指定された機器の視野（FOV）パラメータを返します。機器はそのNAIF IDコードによって指定されます。

### 引数

  * `instid`: 機器のNAIF ID
  * `room`: 返される最大ベクトル数（デフォルト: 10）
  * `shapelen`: 文字列 `shape` に利用可能なスペース（デフォルト: 128）
  * `framelen`: 文字列 `frame` に利用可能なスペース（デフォルト: 128）

### 出力

次の要素からなるタプルを返します。

  * `shape`: 機器のFOV形状
  * `frame`: FOVベクトルが定義されているフレームの名前
  * `bsight`: ボアサイトベクトル
  * `bounds`: FOV境界ベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getfov_c.html)
