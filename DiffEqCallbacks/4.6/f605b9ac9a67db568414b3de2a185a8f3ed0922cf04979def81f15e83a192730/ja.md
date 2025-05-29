```julia
AdaptiveProbIntsUncertainty(order, save = true)
```

[ProbInts](https://arxiv.org/abs/1506.04592)メソッドは、不確実性定量化のためにODEを関連するSDEに変換することを含み、ノイズはタイムステップとアルゴリズムの順序に関連しています。

`AdaptiveProbIntsUncertainty`は、適応時間ステッピングメソッド内の誤差推定を使用して、各ステップで`σ`を推定するより自動化された形の`ProbIntsUncertainty`です。

## 引数

  * `order`はODEソルバーアルゴリズムの順序です。
  * `save`は、このコールバックが保存動作を制御するかどうかを選択するためのものです。一般的に、コールバックセットにコールバックをスタックしていない限り、これは真です。

## 参考文献

Conrad P., Girolami M., Särkkä S., Stuart A., Zygalakis. K, Probability Measures for Numerical Solutions of Differential Equations, arXiv:1506.04592
