```
evaluate(f, u, dt, series, reduce_order_by=0)
```

B系列 `series` を、ベクトル場 `f` と従属変数 `u` を用いた常微分方程式 $u'(t) = f(u(t))$ に特化して評価します。時間ステップサイズ `dt` に対してです。

ここで、`u` は記号変数のベクトルであり、`f` はこれらの変数における表現のベクトルであると仮定されています。プレーンB系列の場合、`f` は変数 `u` の表現のベクトルのタプルでなければなりません。色付き木を持つB系列の場合、`f` は変数 `u` の表現のベクトルのタプルでなければなりません。現在、次の記号変数がサポートされています。

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), および
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)

`dt` の累乗は `reduce_order_by` によって制御でき、根付き木 `t` の通常の `order(t)` とは異なるものにすることができます。これは、B系列係数が $h fₕ$ のものであり、すなわち `dt` の追加の累乗を含む [`modified_equation`](@ref)s や [`modifying_integrator`](@ref)s の文脈で便利です。この場合、ベクトル場のB系列は `reduce_order_by = 1` を使用して取得できます。

# 参考文献

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
