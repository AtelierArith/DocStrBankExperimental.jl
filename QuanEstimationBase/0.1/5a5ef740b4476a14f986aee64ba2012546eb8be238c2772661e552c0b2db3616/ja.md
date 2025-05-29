```
ode(tspan::AbstractVector, ρ0::AbstractMatrix, H0::AbstractVector, dH::AbstractVector; decay::Union{AbstractVector, Nothing}=nothing, Hc::Union{AbstractVector, Nothing}=nothing, ctrl::Union{AbstractVector, Nothing}=nothing)
```

密度行列の動力学は次の形をしています： $\partial_t\rho=-i[H,\rho]+\sum_i \gamma_i\left(\Gamma_i\rho\Gamma^{\dagger}_i-\frac{1}{2}\left\{\rho,\Gamma^{\dagger}_i \Gamma_i \right\}\right)$。ここで、$\rho$は進化した密度行列、$H$は系のハミルトニアン、$\Gamma_i$と$\gamma_i$は$i\mathrm{th}$の減衰演算子と対応する減衰率です。

  * `tspan`: 進化のための時間の長さ。
  * `ρ0`: 初期状態（密度行列）。
  * `H0`: 自由ハミルトニアン。
  * `dH`: 推定される未知のパラメータに関する自由ハミルトニアンの導関数。例えば、dH[0]は最初のパラメータに関する導関数ベクトルです。
  * `decay`: 減衰演算子と対応する減衰率。入力ルールはdecay=[[$\Gamma_1$, $\gamma_1$], [$\Gamma_2$, $\gamma_2$],...]であり、ここで$\Gamma_1$ $(\Gamma_2)$は減衰演算子を表し、$\gamma_1$ $(\gamma_2)$は対応する減衰率です。
  * `Hc`: 制御ハミルトニアン。
  * `ctrl`: 制御係数。
