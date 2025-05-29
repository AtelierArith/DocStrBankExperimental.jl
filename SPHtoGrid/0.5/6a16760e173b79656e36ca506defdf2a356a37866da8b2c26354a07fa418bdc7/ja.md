```
jγ_PE04(rho_cgs::Real, T_K::Real, α_p::Real, Eγ::Real; 
        Xcr::Real=0.5, xH::Real=0.752)
```

光子エネルギー `Eγ` [GeV] におけるガンマ線放射率は、特性 `rho_cgs` [g/cm^3] と `T_K` [K] を持つ熱ガスのためのものです。熱エネルギー密度の割合 `Xcr` としてエネルギースロープ `α_p` を持つCR陽子スペクトルを設定します。放射率は単位 [GeV cm^-3 s^-1] で返されます。Pfrommer&Enßlin (2004), Eq. 19 を参照してください。

## 関数引数:

  * `rho_cgs`: SPH粒子密度 [g/cm^3]
  * `T_K`: SPH粒子温度 [K]
  * `α_p`: 陽子エネルギースペクトルのスロープ `S ~ 2.0 - 2.5`
  * `Eγ`: 光子エネルギー [GeV]
  * `Xcr`: CR陽子と熱圧の比
  * `xH`: シミュレーションにおける水素質量分率

## マッピング設定

視線に沿った平均値のために:

  * `weights`: `rho` (密度で重み付け)
  * `reduce_image`: `true`

視線に沿った積分、すなわち表面輝度のために:

  * `weights`: [`part_weight_physical`](@ref)
  * `reduce_image`: `false`

```
