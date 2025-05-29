```
ModelDataGrid
```

グリッドの定義を含む構造体で、定義する入力変数とその値を含みます。

# フィールド:

  * dfs: モデルのグリッドからの個々の進化トラック情報を含むDataFrameの多次元配列。これはload_grid関数で populated されます。
  * inputs: トラックからのパスのパスを含むStringベクターのベクター。(TODO 例を示す)
  * input_names: グリッドの各パラメータの名前を含むSymbolのベクター。
  * input_values: 入力を浮動小数点数に解析した結果。
  * EEPs: 同等進化ポイントを表す整数の配列（Dotter, 2016を参照）。
  * Xc_TAMS: TAMSを定義する中央水素の限界を示す浮動小数点数。
