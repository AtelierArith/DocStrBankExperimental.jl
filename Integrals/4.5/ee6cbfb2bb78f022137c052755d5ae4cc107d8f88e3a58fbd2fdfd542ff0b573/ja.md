```
HCubatureJL(; norm=norm, initdiv=1, buffer = nothing)
```

HCubature.jlからの多次元「h適応」積分。このメソッドは、オプションの引数`initdiv`と`norm`も受け取ります。これらは、積分領域の各次元が分割される初期セグメント数と、誤差を計算するためのノルムです。最後に、`buffer`キーワードが設定されている場合（例：`buffer=true`）、複数の積分に再利用するためのバッファが割り当てられ、`integrand_prototype`が提供されていない限り、被積分関数を評価する必要があるかもしれません。`hcubature/hquadrature`への`buffer`キーワードとは異なり、これは自動的に処理されるため、バッファを割り当てる必要はありません。

## 参考文献

```tex
@article{genz1980remarks,
title={Remarks on algorithm 006: An adaptive algorithm for numerical integration over an N-dimensional rectangular region},
author={Genz, Alan C and Malik, Aftab Ahmad},
journal={Journal of Computational and Applied mathematics},
volume={6},
number={4},
pages={295--302},
year={1980},
publisher={Elsevier}
}
```
