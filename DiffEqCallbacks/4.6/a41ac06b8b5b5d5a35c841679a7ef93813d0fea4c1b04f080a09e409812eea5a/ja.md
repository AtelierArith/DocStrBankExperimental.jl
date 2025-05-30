```julia
IntegratingCallback(integrand_func,
    integrand_values::IntegrandValues,
    cache = nothing)
```

関数 `integrand_func(u, t, integrator)` を定義することができ、これは問題の tspan にわたって Integral(integrand_func(u(t),t)dt を返します。

## 引数

  * `integrand_func(out, u, t, integrator)` はインプレース問題用、`out = integrand_func(u, t, integrator)` はアウトオブプレース問題用です。dG/dp を計算するための積分内の量を返します。アウトオブプレース問題の場合、これは出力を割り当てる必要があります（`u` へのビューではなく）。
  * `integrand_values::IntegrandValues` は `integrand_func` が返す型です。すなわち、`integrand_func(t, u, integrator)::integrandType` です。これは `IntegrandValues(integrandType)` を介して指定されます。つまり、`integrand_func` が出力する型（またはそれに互換性のある型）を指定します。
  * `integrand_prototype` は積分関数からの出力のプロトタイプです。

出力された値は `integrand_values` に保存されます。値は `integrand_values.integrand` を介して見つけられます。

!!! 注     このメソッドは現在、10 次以下の ODE ソルバーに制限されています。他のソルバーが必要な場合は、問題をオープンしてください。
