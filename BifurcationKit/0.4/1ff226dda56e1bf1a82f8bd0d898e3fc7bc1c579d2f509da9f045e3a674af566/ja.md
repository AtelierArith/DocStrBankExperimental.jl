```julia
struct BorderingBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}, Ttol} <: BifurcationKit.AbstractBorderedLinearSolver
```

この構造体は、ボーダリング法に基づくボーダー付き線形ソルバーを提供するために使用されます。オプションを使用すると、精度を満たすためにボーダリング削減のシーケンスをトリガーできます。

# 参考文献

これは、Govaerts, W. “Stable Solvers and Block Elimination for Bordered Systems.” SIAM Journal on Matrix Analysis and Applications 12, no. 3 (July 1, 1991): 469–83. https://doi.org/10.1137/0612034 におけるソルバー BEC + k です。

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: ボーダリング法のための線形ソルバー。デフォルト: nothing
  * `tol::Any`: 精度をチェックするための許容誤差。デフォルト: 1.0e-12
  * `check_precision::Bool`: 線形解の精度をチェックしますか？デフォルト: true
  * `k::Int64`: 許容誤差を達成するための再帰の数。デフォルト: 1

# コンストラクタ

  * `BorderingBLS(ls)` というシンプルなコンストラクタがあり、ここで `ls` は線形ソルバーです。例えば `ls = DefaultLS()` のように使用します。
  * キーワード引数を使用してそのようなソルバーを作成できます。例えば `BorderingBLS(solver = DefaultLS(), tol = 1e-4)` のようにします。
