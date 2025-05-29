```
ImplicitFreeSurface(; solver_method=:Default, gravitational_acceleration=g_Earth, solver_settings...)
```

暗黙の自由表面ソルバーを返します。暗黙の自由表面方程式は次のようになります。

$$
\left [ 𝛁_h ⋅ (H 𝛁_h) - \frac{1}{g Δt^2} \right ] η^{n+1} = \frac{𝛁_h ⋅ 𝐐_⋆}{g Δt} - \frac{η^{n}}{g Δt^2} ,
$$

ここで、$η^n$は$n$番目の時間ステップにおける自由表面の高さ、$H$は深さ、$g$は重力加速度、$Δt$は時間ステップ、$𝛁_h$は水平勾配演算子、$𝐐_⋆$は予測速度場$𝐮_⋆$に関連するバロトロピック体積フラックスです。すなわち、

$$
𝐐_⋆ = \int_{-H}^0 𝐮_⋆ \, 𝖽 z ,
$$

ここで

$$
𝐮_⋆ = 𝐮^n + \int_{t_n}^{t_{n+1}} 𝐆ᵤ \, 𝖽t .
$$

この方程式は一般に[`ConjugateGradientSolver`](@ref)を使用して解くことができますが、特別な場合には他のソルバーを呼び出すこともできます。

$$
H
$$

が一定である場合、全体を割ることで次のようになります。

$$
\left ( ∇^2_h - \frac{1}{g H Δt^2} \right ) η^{n+1}  = \frac{1}{g H Δt} \left ( 𝛁_h ⋅ 𝐐_⋆ - \frac{η^{n}}{Δt} \right ) .
$$

したがって、$H$が一定であり、$x$および$y$方向に規則的な間隔のグリッド上では、自由表面は[`FFTBasedPoissonSolver`](@ref)を使用して取得できます。

`solver_method`は次のいずれかです：

  * `:FastFourierTransform`は[`FFTBasedPoissonSolver`](@ref)用
  * `:HeptadiagonalIterativeSolver`は[`HeptadiagonalIterativeSolver`](@ref)用
  * `:PreconditionedConjugateGradient`は[`ConjugateGradientSolver`](@ref)用

デフォルトでは、グリッドが水平方向に規則的な間隔を持つ場合、`:FastFourierTransform`が選択され、それ以外の場合は`:HeptadiagonalIterativeSolver`が選択されます。
