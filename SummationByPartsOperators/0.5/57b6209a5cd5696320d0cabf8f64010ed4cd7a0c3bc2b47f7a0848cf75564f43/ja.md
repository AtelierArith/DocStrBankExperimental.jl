```
upwind_operators(periodic_derivative_operator;
                 derivative_order = 1, accuracy_order,
                 xmin, xmax, N,
                 mode = FastMode())
```

[`periodic_derivative_operator`](@ref) によって構築された演算子から [`PeriodicUpwindOperators`](@ref) を作成します。キーワード引数は直接 [`periodic_derivative_operator`](@ref) に渡されます。

## 例

```jldoctest
julia> D = upwind_operators(periodic_derivative_operator, accuracy_order = 2,
                            xmin = 0//1, xmax = 8//1, N = 8)
Upwind SBP 一階導関数演算子の次数 2 が [0//1, 7//1] のグリッド上で 8 ノードを使用して構築され、
Fornberg1998 の係数を使用しています。

julia> D.minus
周期的な一階導関数演算子の次数 2 が [0//1, 8//1] のグリッド上で 8 ノードを使用して構築され、
左に 2 ノード、右に 0 ノードのステンシルを持ち、Fornberg (1998) の係数を使用しています。
  有限差分公式における重みの計算。
  SIAM Rev. 40.3, pp. 685-691.

julia> D.plus
周期的な一階導関数演算子の次数 2 が [0//1, 8//1] のグリッド上で 8 ノードを使用して構築され、
左に 0 ノード、右に 2 ノードのステンシルを持ち、Fornberg (1998) の係数を使用しています。
  有限差分公式における重みの計算。
  SIAM Rev. 40.3, pp. 685-691.
```

```julia
julia> Matrix(D.central)
8×8 Matrix{Rational{Int64}}:
  0//1   1//1  -1//4   0//1   0//1   0//1   1//4  -1//1
 -1//1   0//1   1//1  -1//4   0//1   0//1   0//1   1//4
  1//4  -1//1   0//1   1//1  -1//4   0//1   0//1   0//1
  0//1   1//4  -1//1   0//1   1//1  -1//4   0//1   0//1
  0//1   0//1   1//4  -1//1   0//1   1//1  -1//4   0//1
  0//1   0//1   0//1   1//4  -1//1   0//1   1//1  -1//4
 -1//4   0//1   0//1   0//1   1//4  -1//1   0//1   1//1
  1//1  -1//4   0//1   0//1   0//1   1//4  -1//1   0//1
```
