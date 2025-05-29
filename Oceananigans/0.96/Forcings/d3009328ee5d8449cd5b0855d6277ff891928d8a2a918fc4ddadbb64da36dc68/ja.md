```
Relaxation(; rate, mask=onefunction, target=zerofunction)
```

指定された`rate`で`target(X..., t)`にフィールドを復元する`Forcing`を返します。領域は`mask(X...)`で指定されます。

関数`onefunction`と`zerofunction`はそれぞれ常に1と0を返します。したがって、デフォルトの`mask`は全体のドメインをカバーせず、デフォルトの`target`はゼロです。

# 例

  * 時間スケール"3600"でフィールドをゼロに復元します（シミュレーションの時間単位が秒の場合、1時間に相当します）。

```jldoctest relaxation
using Oceananigans

damping = Relaxation(rate = 1/3600)

# 出力
Relaxation{Float64, typeof(Oceananigans.Forcings.onefunction), typeof(Oceananigans.Forcings.zerofunction)}
├── rate: 0.0002777777777777778
├── mask: 1
└── target: 0
```

  * 時間スケール"60"でドメインの下部1/4内の線形z勾配にフィールドを復元します（シミュレーションの時間単位が秒の場合、1分に相当します）。

```jldoctest relaxation
dTdz = 0.001 # ⁰C m⁻¹, 温度勾配

T₀ = 20 # ⁰C, z=0での表面温度

Lz = 100 # m, ドメインの深さ

bottom_sponge_layer = Relaxation(; rate = 1/60,
                                   target = LinearTarget{:z}(intercept=T₀, gradient=dTdz),
                                   mask = GaussianMask{:z}(center=-Lz, width=Lz/4))

# 出力
Relaxation{Float64, GaussianMask{:z, Float64}, LinearTarget{:z, Float64}}
├── rate: 0.016666666666666666
├── mask: exp(-(z + 100.0)^2 / (2 * 25.0^2))
└── target: 20.0 + 0.001 * z
```
