```
xfmsta(input_state, input_coord_sys, output_coord_sys, body)
```

座標系間で状態を変換します。

### 引数

  * `input_state`: 入力状態
  * `input_coord_sys`: 現在の（入力）座標系
  * `output_coord_sys`: 希望する（出力）座標系
  * `body`: 座標に関連付けられた天体の名前またはNAIF ID（該当する場合）

### 出力

変換された出力状態を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/xfmsta_c.html)
