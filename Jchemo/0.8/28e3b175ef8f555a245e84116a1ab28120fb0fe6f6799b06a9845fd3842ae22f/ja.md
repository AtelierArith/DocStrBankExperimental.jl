```
kpol(X, Y; kwargs...)
```

多項式カーネルグラム行列を計算します。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (m, p)。

キーワード引数：

  * `gamma` : 多項式のスケール。
  * `coef0` : 多項式のオフセット。
  * `degree` : 多項式の次数。

サイズがそれぞれ (n, p) と (m, p) の行列 `X` と `Y` が与えられた場合、関数は (n, m) のグラム行列を返します：

  * K(X, Y) = Phi(X) * Phi(Y)'。

2つのベクトル x と y の間の多項式カーネルは、(`gamma` * (x' * y) + `coef0`)^`degree` によって計算されます。

## 参考文献

Scholkopf, B., Smola, A.J., 2002. Learning with kernels: support  vector machines, regularization, optimization, and beyond, Adaptive  computation and machine learning. MIT Press, Cambridge, Mass.

## 例

```julia
using Jchemo
X = rand(5, 3)
Y = rand(2, 3)
kpol(X, Y; gamma = .1, coef0 = 10, degree = 3)
```
