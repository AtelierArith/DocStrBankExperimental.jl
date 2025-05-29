```
exportImage(filename, im, colorm; vmin, vmax, normalize, pixelResizeFactor)
```

画像データ（2次元 Colorant 配列）`im`を`filename`（パス）として、カラーマップ`colorm`（デフォルト: grays）で色付けしてエクスポートします。

カラーマップは、Colorantsのベクターとして直接指定できます。あるいは、カラーマップの名前を含む文字列を指定することで、ColorSchemesからのカラーマップ（0から1までのアルファグラデーションが追加されたもの）を使用できます。既存のカラーマップは`existing_cmaps()`を使用して見つけることができます。よく使用されるカラーマップは`important_cmaps()`を使用して見つけることができます。カスタマイズされたアルファグラデーションを持つカラーマップは`RGBAGradient()`を使用して構築できます。

さらに、キーワード引数:

  * `vmin`と`vmax`（デフォルト: 0.0および1.0）：浮動小数点数、色付けのための左および右の制限
  * `normalize`（デフォルト: true）：ブール値、trueの場合はデータを[0,1]に正規化
  * `pixelResizeFactor`（デフォルト: 1）：整数、各データポイントに対してプロットされるピクセルの数
