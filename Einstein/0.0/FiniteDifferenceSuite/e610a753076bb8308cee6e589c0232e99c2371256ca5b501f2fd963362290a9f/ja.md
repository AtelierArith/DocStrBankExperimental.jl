```
fdm_weights_fornberg([TR=Float64], order::Integer, x0::Real, x::AbstractVector; 
                         hermite::Bool=false)
```

任意次数の導関数の有限差分重みをFornbergアルゴリズムを使用して計算します。 [SciML/MethodOfLines.jl](https://github.com/SciML/MethodOfLines.jl)から取得。

# 引数

  * `TR`: 重みの型パラメータ（デフォルトはx0の型）
  * `order`: 近似する導関数の次数
  * `x0`: 導関数を近似する点
  * `x`: 近似に使用するグリッドポイント
  * `hermite`: 一次導関数の値を含めるかどうか（エルミート有限差分）

# 戻り値

`hermite == false`の場合:

  * `Vector{TR}`: 標準有限差分の重み

`hermite == true`の場合:

  * `Tuple{Vector{TR}, Vector{TR}}`: エルミート有限差分の重み

# 要件

  * 標準有限差分の場合: N > order
  * エルミート有限差分の場合: N > order/2 + 1

ここでNはxの長さです。

# 例

```julia
# 一次導関数の標準中心差分
x = [-1.0, 0.0, 1.0]
w = fdm_weights_fornberg(1, 0.0, x)
# 約[-0.5, 0.0, 0.5]を返します

# 二次導関数の前方差分
x = [0.0, 1.0, 2.0, 3.0]
w = fdm_weights_fornberg(2, 0.0, x)

# 三次導関数のエルミート有限差分
x = [-1.0, 0.0, 1.0]
w_f, w_d = fdm_weights_fornberg(3, 0.0, x, hermite=true)
```

# 参考文献

  * [MethodOfLines.jl/src/discretization/schemes/fornberg*calculate*weights.jl at master · SciML/MethodOfLines.jl](https://github.com/SciML/MethodOfLines.jl/blob/master/src/discretization/schemes/fornberg_calculate_weights.jl)
  * [fornberg1988generation](@citet*)
  * [fornberg2021algorithm](@citet*)
  * [Fornberg1998](@citet*)
  * [precision - Numerical derivative and finite difference coefficients: any update of the Fornberg method? - Computational Science Stack Exchange](https://scicomp.stackexchange.com/questions/11249/numerical-derivative-and-finite-difference-coefficients-any-update-of-the-fornb)

```
