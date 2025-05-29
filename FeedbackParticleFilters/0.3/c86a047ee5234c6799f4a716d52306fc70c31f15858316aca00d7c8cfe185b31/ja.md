```
DifferentialRKHSMethodS1(epsilon, lambda)
```

円上の微分損失再生カーネルヒルベルト空間 (RKHS) メソッド、[1] のセクション III から適応。カーネルはフォン・ミーゼスカーネルです。

### パラメータ

  * `kappa`: フォン・ミーゼスカーネルのスケールパラメータ。大きな値は狭いカーネルを生成します。
  * `lambda`: 正則化パラメータ、[1] の式 20

### 参考文献

[1] Radhakrishnan, A. & and Meyn, S. (2018). Feedback particle filter design using a differential-loss reproducing kernel Hilbert space. 2018 Annual American Control Conference (ACC). IEEE. https://doi.org/10.23919/ACC.2018.8431689
