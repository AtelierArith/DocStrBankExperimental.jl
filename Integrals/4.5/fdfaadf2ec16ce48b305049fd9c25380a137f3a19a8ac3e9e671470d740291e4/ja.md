```
QuadGKJL(; order = 7, norm = norm, buffer = nothing)
```

QuadGK.jlによる1次元ガウス-クロンロッド積分。このメソッドは、オプションの引数`order`と`norm`も受け取ります。これらはそれぞれ、積分則の次数と誤差を計算するためのノルムです。最後に、`buffer`キーワードが設定されている場合（例：`buffer=true`）、複数の積分のために再利用するバッファを割り当て、`integrand_prototype`が提供されていない限り、被積分関数を評価する必要があるかもしれません。`quadgk`の`segbuf`キーワードとは異なり、このバッファは自動的に処理されるため、手動で割り当てる必要はありません。

## 参考文献

```tex
@article{laurie1997calculation,
title={Calculation of Gauss-Kronrod quadrature rules},
author={Laurie, Dirk},
journal={Mathematics of Computation},
volume={66},
number={219},
pages={1133--1145},
year={1997}
}
```
