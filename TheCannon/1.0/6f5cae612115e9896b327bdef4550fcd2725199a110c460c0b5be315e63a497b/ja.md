```
expand_labels(labels; quadratic=true)
```

`labels`が`Vector`の場合、その二次（または線形）展開を返します。`labels`が`Matrix`の場合、`labels`の行の展開からなる行を持つ行列を返します。

これはWheeler+ 2020で$\eta$と呼ばれる変換であり、[Casey+ 2016](https://arxiv.org/abs/1603.03040)では「ベクトル化関数」として言及されています。
