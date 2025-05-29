```
x_ray_emissivity(T_keV::Vector{<:Real}, 
                 rho_cgs::Vector{<:Real},
                 metalicity::Union{Vector{Float64, Nothing}}=nothing; 
                 E0::Real=0.1, E1::Real=2.4, 
                 xH::Real=0.752,
                 cooling_function::Bool=false,
                 z::Real=0.0)
```

温度 `T_keV` が $keV$ の粒子に対するX線放射率と、密度 `rho_cgs` が $g/cm^3$ です。利用可能であれば、ガス中の `metalicity` も追加できます。 `Emin` と `Emax` は観測の最小および最大エネルギーを示します。 `xH` はシミュレーションで使用される水素の割合を示します。

# 戻り値

単位 [erg/s/cm^3] のX線放射率。

## 引数:

  * `T_keV`: SPH粒子の温度 [keV]
  * `m_cgs`: SPH粒子の質量 [g]
  * `rho_cgs`: SPH粒子の密度 [g/cm^3]
  * `E0`: X線スペクトルの最小光子エネルギー [keV]
  * `E1`: X線スペクトルの最大光子エネルギー [keV]
  * `xH`: シミュレーションにおける水素質量比

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`

```
