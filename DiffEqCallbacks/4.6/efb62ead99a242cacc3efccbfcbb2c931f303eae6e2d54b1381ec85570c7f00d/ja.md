```julia
IntegratingCallback(integrand_func,
    integrand_values::IntegrandValues, integrand_prototype)
```

関数 `integrand_func(u, t, integrator)::typeof(integrand_prototype)` を定義し、問題の tspan にわたって Integral(integrand_func(u(t),t)dt を返すようにします。

## 引数

  * `integrand_func(out, u, t, integrator)` はインプレース問題用で、`out = integrand_func(u, t, integrator)` はアウトオブプレース問題用です。dG/dp を計算するための積分内の量を返します。アウトオブプレース問題の場合、出力は `u` へのビューではなく、出力を割り当てる必要があります。
  * `integrand_values::IntegrandValues` は `integrand_func` が返す型、すなわち `integrand_func(t, u, integrator)::integrandType` です。これは `IntegrandValues(integrandType)` を介して指定され、`integrand_func` が出力する型（またはより高い互換性のある型）を与えます。
  * `integrand_prototype` は積分関数からの出力のプロトタイプです。

出力された値は `integrand_values` に保存されます。値は `integrand_values.integrand` を介して見つけられます。

!!! 注     このメソッドは現在、10 次以下の ODE ソルバーに制限されています。他のソルバーが必要な場合は、問題をオープンしてください。

```
`integrand_func` がインプレースの場合、`cache` を使用して `integrand_func` の出力を保存する必要があります。
```
