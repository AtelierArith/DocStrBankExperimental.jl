# インテリアポイントニュートン

## コンストラクタ

```jl
IPNewton(; linesearch::Function = Optim.backtrack_constrained_grad,
         μ0::Union{Symbol,Number} = :auto,
         show_linesearch::Bool = false)
```

初期バリアペナルティ係数 `μ0` は数値として選択することも、アルゴリズムにその値を決定させるために `:auto` に設定することもできます。詳細は `initialize_μ_λ!` を参照してください。

*注*: 制約付き最適化問題に対しては、`optimize` に渡されるオプションで `allow_f_increases` と `successive_f_tol` を常に有効にすることをお勧めします。デフォルトは `Optim.Options(allow_f_increases = true, successive_f_tol = 2)` に設定されています。

2018年2月現在、ラインサーチアルゴリズムは制約付きインテリアポイント法に特化しています。将来的には `LineSearches.jl` からのより多くのアルゴリズムをサポートすることを期待しています。

## 説明

`IPNewton` メソッドは、非線形の制約付き最適化問題を解決するためのインテリアポイントプライマル-デュアルニュートンアルゴリズムを実装しています。制約付き最適化のためのインテリアポイント法については、Nocedal と Wright (Ch. 19, 2006) を参照してください。

## 参考文献

このアルゴリズムは [Tim Holy によって最初に書かれました](https://github.com/JuliaNLSolvers/Optim.jl/pull/303) (@timholy, tim.holy@gmail.com)。

  * J Nocedal, SJ Wright (2006), Numerical optimization, second edition. Springer.
  * A Wächter, LT Biegler (2006), On the implementation of an interior-point filter line-search algorithm for large-scale nonlinear programming. Mathematical Programming 106 (1), 25-57.
