```
CubatureJLh(; error_norm=Cubature.INDIVIDUAL)
```

Cubature.jlによる多次元h適応積分。`error_norm`はベクトル値の被積分関数に対する収束基準を指定します。デフォルトは`Cubature.INDIVIDUAL`で、他のオプションには`Cubature.PAIRED`、`Cubature.L1`、`Cubature.L2`、または`Cubature.LINF`があります。

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
