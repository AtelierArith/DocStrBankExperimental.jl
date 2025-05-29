# BFGS

## コンストラクタ

```julia
BFGS(; alphaguess = LineSearches.InitialStatic(),
       linesearch = LineSearches.HagerZhang(),
       initial_invH = x -> Matrix{eltype(x)}(I, length(x), length(x)),
       manifold = Flat())
```

## 説明

`BFGS` メソッドは、Nocedal と Wright (sec. 8.1, 1999) に記載されている Broyden-Fletcher-Goldfarb-Shanno アルゴリズムを実装しています。また、Broyden (1970)、Fletcher (1970)、Goldfarb (1970)、Shanno (1970) の4つの個別の論文も参照されています。これは準ニュートン法であり、過去の近似値と勾配を使用してヘッセ行列の近似を更新します。高次元の問題により適したアルゴリズムである制限付きメモリバリアント `LBFGS` も参照してください。

## 参考文献

  * Wright, S. J. and J. Nocedal (1999), Numerical optimization. Springer Science 35.67-68: 7.
  * Broyden, C. G. (1970), The convergence of a class of double-rank minimization algorithms, Journal of the Institute of Mathematics and Its Applications, 6: 76–90.
  * Fletcher, R. (1970), A New Approach to Variable Metric Algorithms, Computer Journal, 13 (3): 317–322,
  * Goldfarb, D. (1970), A Family of Variable Metric Updates Derived by Variational Means, Mathematics of Computation, 24 (109): 23–26,
  * Shanno, D. F. (1970), Conditioning of quasi-Newton methods for function minimization, Mathematics of Computation, 24 (111): 647–656.
