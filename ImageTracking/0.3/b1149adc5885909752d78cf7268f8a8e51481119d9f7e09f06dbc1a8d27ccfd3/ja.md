```
A, B, C = polynomial_expansion(implementation, img, neighbourhood, σ)
```

2D関数の点の近傍を多項式で近似したときの多項式係数を返します。展開は次のようになります: f(x) = x'Ax + B'x + C

# オプション

このタイプのフィールドに関するさまざまなオプションが以下に詳述されています。

## `implementation`の選択肢

実装を選択します（`::MatrixImplementation`対`::ConvolutionImplementation`）。行列実装は、他のより高速な実装を検証するための有用な参照として機能します。

## `img`の選択肢

多項式展開を見つけるグレースケール（Float）画像。

## `window_size`の選択肢

各ピクセルの多項式展開を見つけるために使用されるピクセル近傍のサイズを決定します。大きな値は、画像がより滑らかな表面で近似され、より堅牢なアルゴリズムとよりぼやけた動きの場を生み出すことを意味します。総サイズは`2*window_size + 1`に等しいです。

## `σ`の選択肢

多項式展開で近似する目的で画像を滑らかにするために使用されるガウスの標準偏差。

## 参考文献

Farnebäck, G.: Polynomial Expansion for Orientation and Motion Estimation. PhD thesis, Linköping University, Sweden, SE-581 83 Linköping, Sweden (2002) Dissertation No 790, ISBN 91-7373-475-6.
