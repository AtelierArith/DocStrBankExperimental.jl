```
VectorInvariant(; vorticity_scheme = EnstrophyConserving(),
                  vorticity_stencil = VelocityStencil(),
                  vertical_scheme = EnergyConserving(),
                  divergence_scheme = vertical_scheme,
                  kinetic_energy_gradient_scheme = divergence_scheme,
                  upwinding  = OnlySelfUpwinding(; cross_scheme = divergence_scheme),
                  multi_dimensional_stencil = false)
```

ベクトル不変モーメント輸送スキームを返します。

# キーワード引数

  * `vorticity_scheme`: 渦度の `Center` 再構成に使用されるスキーム。デフォルト: `EnstrophyConserving()`。オプション:

      * `UpwindBiased()`
      * `WENO()`
      * `EnergyConserving()`
      * `EnstrophyConserving()`
  * `vorticity_stencil`: `WENO` スキームの滑らかさ指標に使用されるステンシル。デフォルト: `VelocityStencil()`。オプション:

      * `VelocityStencil()` (水平速度に基づく滑らかさ)
      * `DefaultStencil()` (再構成される変数に基づく滑らかさ)
  * `vertical_scheme`: 水平モーメントの垂直輸送に使用されるスキーム。デフォルト: `EnergyConserving()`。
  * `kinetic_energy_gradient_scheme`: 運動エネルギー勾配の再構成に使用されるスキーム。デフォルト: `vertical_scheme`。
  * `divergence_scheme`: 発散フラックスに使用されるスキーム。アップウィンドスキームのみがサポートされています。デフォルト: `vorticity_scheme`。
  * `upwinding`: 発散と運動エネルギー勾配のアップウィンド再構成の処理。デフォルト: `OnlySelfUpwinding()`。オプション:

      * `CrossAndSelfUpwinding()`
      * `OnlySelfUpwinding()`
  * `multi_dimensional_stencil`: 渦度、発散、運動エネルギー勾配の再構成に水平の二次元ステンシルを使用するかどうか。現在、「接線」方向は5次中心WENO再構成を使用します。デフォルト: false

# 例

```jldoctest
julia> using Oceananigans

julia> VectorInvariant()
Vector Invariant, Dimension-by-dimension reconstruction
 Vorticity flux scheme:
 └── Oceananigans.Advection.EnstrophyConserving{Float64}
 Vertical advection / Divergence flux scheme:
 └── Oceananigans.Advection.EnergyConserving{Float64}
```

```jldoctest
julia> using Oceananigans

julia> VectorInvariant(vorticity_scheme = WENO(), vertical_scheme = WENO(order = 3))
Vector Invariant, Dimension-by-dimension reconstruction
 Vorticity flux scheme:
 ├── WENO(order=5)
 └── smoothness ζ: Oceananigans.Advection.VelocityStencil()
 Vertical advection / Divergence flux scheme:
 ├── WENO(order=3)
 └── upwinding treatment: OnlySelfUpwinding
 KE gradient and Divergence flux cross terms reconstruction:
 └── Centered(order=2)
 Smoothness measures:
 ├── smoothness δU: FunctionStencil f = divergence_smoothness
 ├── smoothness δV: FunctionStencil f = divergence_smoothness
 ├── smoothness δu²: FunctionStencil f = u_smoothness
 └── smoothness δv²: FunctionStencil f = v_smoothness
```
