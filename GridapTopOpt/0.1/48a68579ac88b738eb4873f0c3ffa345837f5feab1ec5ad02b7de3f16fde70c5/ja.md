```
struct SmoothErsatzMaterialInterpolation{M<:Vector{<:Number},N<:Vector{<:Number}}
```

単一の境界 $\partial\Omega$ にわたる被積分関数を補間するためのパラメータとメソッドを保持するラッパーです。

例えば、$\int f~\mathrm{d}\Omega = \int I(\varphi)f~\mathrm{d}D$ であり、ここで $\Omega\subset D$ はレベルセット関数 $\varphi$ によって記述され、$I$ は指示関数です。

# 特性

  * `η::M`: ∂Ω にわたる補間または平滑化半径
  * `ϵ::M`: 擬似材料密度
  * `H`: 平滑化されたヘヴィサイド関数
  * `DH`: `H` の導関数
  * `I`: 指示関数
  * `ρ`: $\Omega$ の体積密度を記述する関数（例: $\mathrm{Vol}(\Omega) = \int \rho(\varphi))~\mathrm{d}D)$

# 注意

  * η と ϵ は長さ1のベクトルとして保存されるため、これらの値を更新すると H, DH などに伝播します。
  * インスタンス `m` の η および/または ϵ を更新するには、`m.η .= <VALUE>` を使用します。
  * `η<:Number` と `ϵ<:Number` を指定してインスタンスを作成するための便利なコンストラクタが提供されています。
