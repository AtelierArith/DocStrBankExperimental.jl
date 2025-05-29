```
asymptote_export_S2_signals(filename; points, curves, tangent_vectors, colors, options...)
```

与えられた `points`、`curves`、および `tangent_vectors` を球面 $\mathbb S^2$ に Asymptote にエクスポートします。

# 入力

  * `filename`          Asymptote コードを保存するファイル。

# データのオプション引数

  * `colors`            色の配列の辞書（シンボル `:points`、 `:curves` および `:tvector` によってインデックス付けされており、各エントリは対応するセットの長さと同じ数以上の色を提供する必要があります）。
  * `curves`            球面上の点の `Array` の `Arrays` で、各内部配列は曲線として解釈され、`colors` 内のエントリに伴います。
  * `points`            球面上の点の `Array` の `Arrays` で、各内部配列は点のセットとして解釈され、`colors` 内のエントリに伴います。
  * `tangent_vectors`   タプルの `Array` の `Arrays` で、最初は点、2番目は接ベクトルであり、各ベクトルのセットは `colors` 内のエントリに伴います。

# Asymptote のオプション引数

  * `arrow_head_size`:   （`6.0`）接ベクトルの矢印のサイズ
  * `arrow_head_sizes`  前の値をオーバーライドして、各 `tVector` セットごとに値を指定します。
  * `camera_position`:   （`(1., 1., 0.)`）Asymptote シーン内のカメラの位置
  * `line_width`:        （`1.0`）曲線を描画するために使用される線のサイズ。
  * `line_widths`       前の値をオーバーライドして、各曲線および `tVector` セットごとに値を指定します。
  * `dot_size`:          （`1.0`）点を描画するために使用されるドットのサイズ。
  * `dot_sizes`         前の値をオーバーライドして、各点セットごとに値を指定します。
  * `size`:              （`nothing`）画像サイズのタプル、さもなくば相対サイズ `4cm` が使用されます。
  * `sphere_color`:      （`RGBA{Float64}(0.85, 0.85, 0.85, 0.6)`）データが描画される球の色
  * `sphere_line_color`: （`RGBA{Float64}(0.75, 0.75, 0.75, 0.6)`）球面上の線の色
  * `sphere_line_width`: （`0.5`）球面上の線の線幅
  * `target`:            （`(0.,0.,0.)`）カメラが向いている位置

```
