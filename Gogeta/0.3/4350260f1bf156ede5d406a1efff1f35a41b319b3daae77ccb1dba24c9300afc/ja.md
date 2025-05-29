```
function NN_compress(NN_model::Flux.Chain, U_in, L_in, U_bounds, L_bounds)
```

ニューラルネットワークを事前に計算された境界を使用して圧縮します。

# 引数

  * `NN_model`: 圧縮されるニューラルネットワーク。
  * `U_in`: 入力変数の上限。
  * `L_in`: 入力変数の下限。
  * `U_bounds`: 他のニューロンの上限。
  * `L_bounds`: 他のニューロンの下限。

圧縮されたニューラルネットワークの `Flux.Chain` モデルを返します。
