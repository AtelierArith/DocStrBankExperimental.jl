```
sequential_palette(h, N::Int=100; <keyword arguments>)
```

[Wijffelaars, M., et al. (2008)](http://magnaview.nl/documents/MagnaView-M_Wijffelaars-Generating_color_palettes_using_intuitive_parameters.pdf) によるカラーパレット作成技術を実装します。

カラーマップは、一定の色相でLCHuvカラースペース内のベジェ曲線を使用して形成されます。さらに、開始点と終了点を指定することができ、それらは元の色相に滑らかにブレンドされます。

# 引数

  * N        - 色の数
  * h        - 主な色相 [0,360]
  * c        - 全体の明度コントラスト [0,1]
  * s        - 彩度 [0,1]
  * b        - 明るさ [0,1]
  * w        - 冷暖パラメータ、すなわち開始色の強さ [0,1]
  * d        - 終了色の深さ [0,1]
  * wcolor   - 開始色（暖かさ）
  * dcolor   - 終了色（深さ）
  * logscale - ログ間隔を切り替えるための真偽値
