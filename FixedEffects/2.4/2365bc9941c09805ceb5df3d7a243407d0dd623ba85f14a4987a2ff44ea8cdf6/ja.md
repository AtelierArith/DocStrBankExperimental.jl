固定効果のセットに対する最小二乗問題を解く

`solve_coefficients!(y, fes, w; method = :cpu, maxiter = 10000, double_precision = true, tol = 1e-8)`

$$
\beta = \arg\min_{b} \sum_i w_i(y_i - X_i'b)
$$

を返します。ここで `X` は固定効果 `fes` の行列を示します。

### 引数

  * `y` : `AbstractVector`
  * `fes`: `Vector{<:FixedEffect}`
  * `w`: 重みのベクトル、すなわち `AbstractWeights`
  * `method` : メソッドのための `Symbol`。デフォルトは :cpu です。オプション :gpu は `using CUDA` を必要とします（この場合、`double_precision = false` オプションを使用することを推奨します）。
  * `double_precision::Bool`: 平均を取る操作は Float64 を使用すべきですか？デフォルトは true です。
  * `tol` : 許容誤差。`double_precision = true` の場合はデフォルトで 1e-8、そうでない場合は 1e-6 です。
  * `maxiter` : 最大反復回数
  * `nthreads` : スレッドの数

### 戻り値

  * $$
    \beta
    $$

    : 最小二乗問題の解
  * `iterations`: 反復回数
  * `converged`: アルゴリズムは収束しましたか？

固定効果は一般に一意ではありません。次のように解を標準化します：接続成分内の固定効果の平均はゼロです（最初のものを除く）。これにより、2つの固定効果の場合に一意の解が得られます。

### 例

```julia
using  FixedEffects
p1 = repeat(1:5, inner = 2)
p2 = repeat(1:5, outer = 2)
x = rand(10)
solve_coefficients!(rand(10), [FixedEffect(p1), FixedEffect(p2)])
```
