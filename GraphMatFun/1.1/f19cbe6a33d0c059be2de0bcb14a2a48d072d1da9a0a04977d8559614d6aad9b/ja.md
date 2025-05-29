```
 (graph,crefs)=graph_exp_native_jl(A; input=:A)
```

行列指数関数のネイティブなスケーリングと平方化のためのグラフを作成します。これはJuliaで実装されています。行列 `A` は、Padé近似の長さと適用される平方の数、および係数のタイプを決定するための入力として使用されます。キーワード引数 `input` は、グラフ内の行列の名前を決定します。

**参考文献**

1. N. J. Higham. "Functions of Matrices". SIAM, Philadelphia, PA, 2008. DOI: [10.1137/1.9780898717778](https://doi.org/10.1137/1.9780898717778)
2. N. J. Higham. "The Scaling and Squaring Method for the Matrix Exponential Revisited". SIAM Journal on Matrix Analysis and Applications, 26(4):1179-1193, 2005. DOI: [10.1137/04061101X](https://doi.org/10.1137/04061101X)
3. "Julia's matrix exponential", [at the time of conversion](https://github.com/JuliaLang/julia/blob/697e782ab86bfcdd7fd15550241fe162c51d9f98/stdlib/LinearAlgebra/src/dense.jl#L554).
