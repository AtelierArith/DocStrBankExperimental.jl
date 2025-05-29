```
modifying_integrator(f, u, dt, rk::RungeKuttaMethod, order)
modifying_integrator(f, u, dt,
                     A::AbstractMatrix, b::AbstractVector, c::AbstractVector,
                     order)
```

Runge-Kutta法のButcher係数 `A, b, c` に関する [`modifying_integrator`](@ref) 方程式のB系列を、通常の微分方程式 $u'(t) = f(u(t))$ に対して、指定された `order` まで計算します。ここで、`u` は記号変数のベクトルであり、`f` はこれらの変数における表現のベクトルであると仮定します。プレーンB系列の場合、`f` は変数 `u` における表現のベクトルのタプルでなければなりません。色付き木を持つB系列の場合、`f` は変数 `u` における表現のベクトルのタプルでなければなりません。現在、次の記号変数がサポートされています。

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), および
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)
