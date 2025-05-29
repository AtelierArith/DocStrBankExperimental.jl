`solve_residuals!(y, fes, w; method = :cpu, double_precision = true, tol = 1e-8, maxiter = 10000, )`

$$
y_i - X_i'\beta
$$

を返します。ここで、$\beta = argmin_{b} \sum_i y_i - X_i'b$ であり、`X` は固定効果 `fes` の行列を示します。

### 引数

  * `y` : `AbstractVector` または `AbstractMatrix`
  * `fes`: `Vector{<:FixedEffect}`
  * `w`: 重みのベクトル、すなわち `AbstractWeights`
  * `method` : メソッドのための `Symbol`。デフォルトは :cpu です。オプション :gpu は `using CUDA` または `using Metal` を必要とします（この場合、`double_precision = false` オプションを使用することを推奨します）。
  * `double_precision::Bool`: 平均を取る操作は Float64 を使用すべきですか？デフォルトは true です。
  * `tol` : 許容誤差。`double_precision = true` の場合はデフォルトで 1e-8、そうでない場合は 1e-6 です。
  * `maxiter` : 最大反復回数

### 戻り値

  * `res` : 最小二乗問題の残差
  * `iterations`: 反復回数
  * `converged`: アルゴリズムは収束しましたか？

### 例

```julia
using  FixedEffects
p1 = repeat(1:5, inner = 2)
p2 = repeat(1:5, outer = 2)
solve_residuals!(rand(10), [FixedEffect(p1), FixedEffect(p2)])
```
