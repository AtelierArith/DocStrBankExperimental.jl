```julia
ProbIntsUncertainty(σ, order, save = true)
```

[ProbInts](https://arxiv.org/abs/1506.04592)メソッドは不確実性定量化のために、ODEを関連するSDEに変換することを含み、ここでノイズはタイムステップとアルゴリズムの順序に関連しています。

## 引数

  * `σ`はノイズスケーリングファクターです。`σ`は方程式の単一ステップにおける誤差の大きさを代表することが推奨されます。そのような値が不明な場合、AdaptiveProbIntsUncertaintyを介して適応的なタイムステッピングアルゴリズムで自動的に推定できます。
  * `order`はODEソルバーアルゴリズムの順序です。
  * `save`はこのコールバックが保存動作を制御するかどうかを選択するためのものです。一般的にこれは真であり、`CallbackSet`にコールバックをスタックする場合を除きます。

## 参考文献

Conrad P., Girolami M., Särkkä S., Stuart A., Zygalakis. K, Probability Measures for Numerical Solutions of Differential Equations, arXiv:1506.04592
