```
Farneback(Args...)
```

Gunnar Farnebackによって開発された密な光学フロー推定のためのメソッドです。これは、画像の多項式表現を使用して、フレーム内のすべての点の光学フローを計算します。多項式展開のアイデアは、2D関数内の点の近傍を多項式で近似することです。変位場は、多項式が平行移動の下でどのように変換されるかに依存して、多項式係数から推定されます。

# オプション

このタイプのフィールドに関するさまざまなオプションが以下に詳述されています。

## `iterations`の選択肢

各点で変位推定アルゴリズムが実行される反復回数です。指定しない場合は、デフォルト値として7回の反復が想定されます。

## `estimation_window`の選択肢

ピクセルの変位を決定する際に情報が統合される近傍のサイズを決定します。総サイズは`2*estimation_window + 1`です。指定しない場合は、デフォルト値として11が想定されます。

## `σ_estimation_window`の選択肢

ピクセルの変位を決定する際に、ピクセルの近傍の寄与を重み付けするために使用されるガウス重み付けフィルタの標準偏差です。指定しない場合は、デフォルト値として9が想定されます。

## `expansion_window`の選択肢

各ピクセルの多項式展開を見つけるために使用されるピクセル近傍のサイズを決定します。大きな値は、画像がより滑らかな表面で近似され、より堅牢なアルゴリズムとよりぼやけた動きのフィールドをもたらします。総サイズは`2*expansion_window + 1`です。指定しない場合は、デフォルト値として6が想定されます。

## `σ_expansion_window`の選択肢

多項式展開で近似する目的で画像を平滑化するために使用されるガウスの標準偏差です。指定しない場合は、デフォルト値として5が想定されます。

# 参考文献

1. Farnebäck G. (2003) Two-Frame Motion Estimation Based on Polynomial Expansion. In: Bigun J., Gustavsson T. (eds) Image Analysis. SCIA 2003. Lecture Notes in Computer Science, vol 2749. Springer, Berlin, Heidelberg
2. Farnebäck, G.: Polynomial Expansion for Orientation and Motion Estimation. PhD thesis, Linköping University, Sweden, SE-581 83 Linköping, Sweden (2002) Dissertation No 790, ISBN 91-7373-475-6.
