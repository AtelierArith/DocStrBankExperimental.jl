```
VEGAS(; nbins = 100, ncalls = 1000, debug=false, seed = nothing)
```

MonteCarloIntegration.jlからの多次元適応モンテカルロ積分。重要度サンプリングを使用して分散を減少させます。このメソッドは、積分領域の各次元が分割される初期のビンの数を示す`nbins`、アルゴリズムの各反復ごとの関数呼び出しの数を示す`ncalls`、およびデバッグ情報を印刷するかどうかを示す`debug`の3つのオプション引数を取ります。

## 制限事項

このアルゴリズムは`Float64`値の関数のみを積分できます。

## 参考文献

```tex
@article{lepage1978new,
title={A new algorithm for adaptive multidimensional integration},
author={Lepage, G Peter},
journal={Journal of Computational Physics},
volume={27},
number={2},
pages={192--203},
year={1978},
publisher={Elsevier}
}
```
