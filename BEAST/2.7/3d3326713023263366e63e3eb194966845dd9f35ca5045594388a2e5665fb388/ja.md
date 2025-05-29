```
RungeKuttaConvolutionQuadrature{T,N,NN}
```

T: 基底関数の値の型。N: ステージの数。NN: N*N。

暗黙のルンゲ・クッタ法を使用して、時間領域で演算子を表現するために、laplaceKernel上で畳み込み quadrature を実行します。

laplaceKernel: ラプラス変数 s の関数で、IntegralOperator を返します。A, b: ブッチャー表からの係数行列とベクトル。Δt: 時間ステップ。zTransformedTermCount: 逆Z変換における項の数。contourRadius: 逆Z変換のための積分輪郭として使用される円の半径。
