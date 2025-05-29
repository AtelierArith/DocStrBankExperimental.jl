```
admm(x0, prox_f!, prox_g!; λ=1., α=1., ϵ_abs=1e-7, ϵ_rel=1e-4, max_iter=1000)
```

目的関数 $f(x) + g(x)$ を最小化します。ここで、$f(x)$ と $g(x)$ はどちらも非滑らかである可能性があり、交互方向法（alternating direction method of multipliers）、またはダグラス-ラッカーフォード分割（Douglas-Rachford splitting）として知られています。交互方向法には2つのハイパーパラメータ `λ` と `α` があります。`λ` は更新ステップのスケーリングを制御し、すなわち擬似ステップサイズであり、増強ラグランジュパラメータの逆数に等しいです。$α ∈ [0,2]$ は緩和パラメータであり、$α < 1$ はアンダーリラクゼーション、$α > 1$ はオーバーリラクゼーションを示します。

#### 引数

  * `x0::AbstractVector`: 初期パラメータ値 (n x 1)
  * `prox_f!::Function` : $f(x)$ の近接作用素
  * `prox_g!::Function` : $g(x)$ の近接作用素
  * `λ::Real`           : 近接スケーリングパラメータ
  * `α::Real`           : 緩和パラメータ
  * `ϵ_abs::Real`       : 絶対許容誤差
  * `ϵ_rel::Real`       : 相対許容誤差
  * `max_iter::Integer` : 最大反復回数

#### 戻り値

  * `x::AbstractVector` : 最小化された値 $∈ dom f$ (n x 1)
  * `z::AbstractVector` : 最小化された値 $∈ dom g$ (n x 1)

```
