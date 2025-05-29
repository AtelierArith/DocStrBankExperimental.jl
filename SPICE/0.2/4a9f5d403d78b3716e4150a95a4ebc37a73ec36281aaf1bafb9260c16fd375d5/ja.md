```
et2lst(et, body, lon, typ, timlen=128, ampmlen=128)
```

与えられたエフェメリスエポックに基づいて、指定された経度の天体の表面上の物体のためのローカルソーラータイムを計算します。

### 引数

  * `et`: J2000エポックからの秒数
  * `body`: 関心のある天体のIDコード
  * `lon`: 表面点の経度（ラジアン）
  * `typ`: 経度のタイプ "PLANETOCENTRIC" など
  * `timlen`: 出力時間文字列のための利用可能なスペース（デフォルト: 128）
  * `ampmlen`: 出力 `ampm` 文字列のための利用可能なスペース（デフォルト: 128）

### 出力

  * `hr`: "24時間" 時計のローカル時間
  * `mn`: 時間を過ぎた分
  * `sc`: 分を過ぎた秒
  * `time`: 24時間時計のローカル時間を示す文字列
  * `ampm`: A.M./P.M.スケールの時間を示す文字列

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/et2lst_c.html)
