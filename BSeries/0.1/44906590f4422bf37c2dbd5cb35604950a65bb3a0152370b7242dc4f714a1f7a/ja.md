```
modified_equation(f, u, dt, series_integrator)
```

B系列を計算します。これは、普通の微分方程式 $u'(t) = f(u(t))$ に関する時間積分法の [`modified_equation`](@ref) で、B系列 `series_integrator` に対して、ベクトル場 `f` と従属変数 `u` を用いて、時間ステップサイズ `dt` で行います。

ここで、`u` は記号変数のベクトルであり、`f` はこれらの変数に対する表現のベクトルであると仮定します。プレーンB系列の場合、`f` は変数 `u` における表現のベクトルのタプルでなければなりません。色付き木を持つB系列の場合、`f` は変数 `u` における表現のベクトルのタプルでなければなりません。現在、次の記号変数がサポートされています。

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), および
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)
