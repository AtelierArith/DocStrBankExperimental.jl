```
struct PDEConstrainedFunctionals{N,A}
```

目的関数、制約、およびそれらの導関数を計算するオブジェクトです。

# 実装

この実装は、補助パラメータ $\varphi$ に関しての積分量の導関数を計算します。

$$
F(u(\varphi),\varphi,\mathrm{d}\Omega_1,\mathrm{d}\Omega_2,...) = \Sigma_{i}\int_{\Omega_i} f_i(\varphi)~\mathrm{d}\Omega
$$

ここで、$u$ は PDE の解であり、暗黙的に $\varphi$ に依存します。これには2つの情報が必要です：

1. $$
    \frac{\partial F}{\partial u}
    $$

    と $\frac{\partial F}{\partial \varphi}$ の計算（[`StateParamIntegrandWithMeasure`](@ref) によって処理されます）。
2. 隣接法を使用して、$\varphi$ と $u$ における $\frac{\partial F}{\partial u} \frac{\partial u}{\partial \varphi}$ の計算（[`AbstractFEStateMap`](@ref) によって処理されます）。すなわち、

    $\frac{\partial F}{\partial u} \frac{\partial u}{\partial \varphi} = -\lambda^\intercal \frac{\partial \mathcal{R}}{\partial \varphi}$

    ここで、$\mathcal{R}$ は残差であり、（線形）隣接問題を解きます：

    $\frac{\partial \mathcal{R}}{\partial u}^\intercal\lambda = \frac{\partial F}{\partial u}^\intercal.$

勾配は次のようになります：$\frac{\partial F}{\partial \varphi} = \frac{\partial F}{\partial \varphi} - \frac{\partial F}{\partial u}\frac{\partial u}{\partial \varphi}$。

# パラメータ

  * `J`: 目的に対応する `StateParamIntegrandWithMeasure`。
  * `C`: 制約に対応する `StateParamIntegrandWithMeasure` のベクトル。
  * `dJ`: 目的の感度の自由度（DoFs）。
  * `dC`: 各制約の感度の自由度（DoFs）。
  * `analytic_dJ`: 解析的目的感度を計算するための `Function`。
  * `analytic_dC`: 解析的目的感度を計算するための `Function` のベクトル。
  * `state_map::A`: 問題の状態マップ。

# 注意

  * `analytic_dJ = nothing` の場合、自動微分が使用されます。
  * `analytic_dC[i] = nothing` の場合、`C[i]` に対して自動微分が使用されます。

```
