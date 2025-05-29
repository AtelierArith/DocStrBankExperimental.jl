```
krbf(X, Y; kwargs...)
```

ラジアル基底関数 (RBF) カーネル Gram 行列を計算します。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (m, p)。

キーワード引数：

  * `gamma` : スケールパラメータ。

サイズがそれぞれ (n, p) と (m, p) の行列 `X` と `Y` が与えられた場合、関数は (n, m) の Gram 行列を返します：

  * K(X, Y) = Phi(X) * Phi(Y)'。

2つのベクトル x と y の間の RBF カーネルは、exp(-`gamma` * ||x - y||^2) によって計算されます。

## 参考文献

Scholkopf, B., Smola, A.J., 2002. Learning with kernels: support vector machines, regularization, optimization, and beyond, Adaptive computation and machine learning. MIT Press, Cambridge, Mass.

## 例

```julia
using Jchemo
X = rand(5, 3)
Y = rand(2, 3)
krbf(X, Y; gamma = .1)
```
