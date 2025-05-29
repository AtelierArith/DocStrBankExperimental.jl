```
modified_equation(f, u, dt, rk::RungeKuttaMethod, order)
modified_equation(f, u, dt,
                  A::AbstractMatrix, b::AbstractVector, c::AbstractVector,
                  order)
```

Runge-Kutta法 `rk` の [`modified_equation`](@ref) のB系列を、普通の微分方程式 $u'(t) = f(u(t))$ に関して、指定された `order` まで計算します。ここで、ベクトル場 `f` と従属変数 `u` に対して、時間ステップサイズ `dt` を用います。

ここで、`u` は記号変数のベクトルであり、`f` はこれらの変数における式のベクトルであると仮定します。プレーンB系列の場合、`f` は変数 `u` における式のベクトルのタプルでなければなりません。色付き木を持つB系列の場合、`f` は変数 `u` における式のベクトルのタプルでなければなりません。現在、次の記号変数がサポートされています。

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), および
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)
