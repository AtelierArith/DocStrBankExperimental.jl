```
VEGAS(; nbins = 100, ncalls = 1000, debug=false)
```

MonteCarloIntegration.jlからの多次元適応モンテカルロ積分。重要度サンプリングを使用して分散を減少させます。このメソッドは、積分領域の各次元が分割される初期ビンの数、アルゴリズムの各イテレーションあたりの関数呼び出しの数、およびデバッグ情報を印刷するかどうかをそれぞれ指定する3つのオプション引数`nbins`、`ncalls`、`debug`を取ります。

## 参考文献

@article{lepage1978new, title={A new algorithm for adaptive multidimensional integration}, author={Lepage, G Peter}, journal={Journal of Computational Physics}, volume={27}, number={2}, pages={192–203}, year={1978}, publisher={Elsevier} }
