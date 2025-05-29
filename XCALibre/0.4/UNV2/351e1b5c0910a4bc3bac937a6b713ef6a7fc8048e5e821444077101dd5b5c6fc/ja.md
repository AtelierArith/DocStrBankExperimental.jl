```
UNV2D_mesh(meshFile; scale=1, integer_type=Int64, float_type=Float64)
```

2D UNVメッシュファイルをXCALibre.jlに読み込み、変換します。

### 入力

  * `meshFile` – メッシュファイルへのパス。

### オプション引数

  * `scale` – メッシュファイルをスケールするために使用されます。例えば、scale=0.001はメッシュをmmからメートルに変換します。デフォルトは1、すなわちスケーリングなしです。
  * `integer_type` - メッシュで使用する整数型を選択します（Int32はGPU実行時に便利かもしれません）。
  * `float_type` - メッシュで使用する浮動小数点型を選択します（Float32はGPU実行時に便利かもしれません）。
