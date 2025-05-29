```
modifying_integrator(f, u, dt, series_integrator)
```

B系列の[`modifying_integrator`](@ref)方程式を計算します。これは、ベクトル場`f`と依存変数`u`に対する常微分方程式$u'(t) = f(u(t))$に関して、B系列`series_integrator`を用いた時間積分法のものです。時間ステップサイズは`dt`です。

ここで、`u`は記号変数のベクトルであり、`f`はこれらの変数に対する式のベクトルであると仮定されています。プレーンB系列の場合、`f`は変数`u`の式のベクトルのタプルでなければなりません。色付き木を持つB系列の場合、`f`は変数`u`の式のベクトルのタプルでなければなりません。現在、次の記号変数がサポートされています。

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), および
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)
