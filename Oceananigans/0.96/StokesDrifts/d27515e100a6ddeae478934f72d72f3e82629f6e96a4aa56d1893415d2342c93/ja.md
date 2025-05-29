```
StokesDrift(; ∂z_uˢ=zerofunction, ∂y_uˢ=zerofunction, ∂t_uˢ=zerofunction,
              ∂z_vˢ=zerofunction, ∂x_vˢ=zerofunction, ∂t_vˢ=zerofunction,
              ∂x_wˢ=zerofunction, ∂y_wˢ=zerofunction, ∂t_wˢ=zerofunction, parameters=nothing)

表面重力波場に対応するストークス漂流速度場の空間と時間の関数のセットを構築します。エンベロープは（潜在的に）水平方向で変化します。

ラグランジアン平均運動量の進化を解決するために、「擬似渦度」のすべての成分が必要です。

```

math 𝛁 × 𝐯ˢ = \hat{\boldsymbol{x}} (∂*y wˢ - ∂*z vˢ) + \hat{\boldsymbol{y}} (∂*z uˢ - ∂*x wˢ) + \hat{\boldsymbol{z}} (∂*x vˢ - ∂*y uˢ)

```

また、$uˢ$、$vˢ$、および$wˢ$の時間微分も必要です。

各関数（例：`∂z_uˢ`）は一般に深さ、水平座標、および時間の関数であることに注意してください。したがって、正しい関数シグネチャはグリッドに依存します。`Flat`水平方向は省略されます。

たとえば、`topology = (Periodic, Flat, Bounded)`のグリッドでは（および`parameters=nothing`の場合）、`∂z_uˢ`は`∂z_uˢ(x, z, t)`を介して呼び出されます。`!isnothing(parameters)`の場合、`∂z_uˢ`は`∂z_uˢ(x, z, t, parameters)`を介して呼び出されます。同様に、`topology = (Periodic, Periodic, Bounded)`のグリッドでは、`parameters=nothing`の場合、`∂z_uˢ`は`∂z_uˢ(x, y, z, t)`を介して呼び出されます。

# 例

グループ速度で$x$方向に移動する波パケット。ストークス漂流を次のように書きます。

```

math uˢ(x, y, z, t) = A(x - cᵍ \, t, y) ûˢ(z)

```

ここで、$A(ξ, η) = \exp{[-(ξ^2 + η^2) / 2δ^2]}$とします。また、$vˢ = 0$であると仮定します。$𝐯ˢ$がストークス漂流のソレノイダル成分を表す場合、この系では非圧縮性の要件から$∂_z wˢ = - ∂_x uˢ = - (∂_ξ A) ûˢ$となり、したがって、$wˢ$が大きな深さでゼロに近づくという仮定の下で、$wˢ = - (∂_ξ A / 2k) ûˢ$が得られます。

```

jldoctest using Oceananigans using Oceananigans.Units

g = 9.81 # 重力加速度

ϵ = 0.1 λ = 100meters  # 水平波長 const k = 2π / λ  # 水平波数 c = sqrt(g / k)  # 位相速度 const δ = 400kilometers  # 波パケットの広がり const cᵍ = c / 2  # 群速度 const Uˢ = ϵ^2 * c

@inline A(ξ, η) = exp(- (ξ^2 + η^2) / 2δ^2)

@inline ∂ξ*A(ξ, η) = - ξ / δ^2 * A(ξ, η) @inline ∂η*A(ξ, η) = - η / δ^2 * A(ξ, η) @inline ∂η*∂ξ*A(ξ, η) = η * ξ / δ^4 * A(ξ, η) @inline ∂²ξ_A(ξ, η) = (ξ^2 / δ^2 - 1) * A(ξ, η) / δ^2

@inline ûˢ(z) = Uˢ * exp(2k * z) @inline uˢ(x, y, z, t) = A(x - cᵍ * t, y) * ûˢ(z)

@inline ∂z*uˢ(x, y, z, t) = 2k * A(x - cᵍ * t, y) * ûˢ(z) @inline ∂y*uˢ(x, y, z, t) = ∂η*A(x - cᵍ * t, y) * ûˢ(z) @inline ∂t*uˢ(x, y, z, t) = - cᵍ * ∂ξ*A(x - cᵍ * t, y) * ûˢ(z) @inline ∂x*wˢ(x, y, z, t) = - 1 / 2k * ∂²ξ*A(x - cᵍ * t, y) * ûˢ(z) @inline ∂y*wˢ(x, y, z, t) = - 1 / 2k * ∂η*∂ξ*A(x - cᵍ * t, y) * ûˢ(z) @inline ∂t*wˢ(x, y, z, t) = + cᵍ / 2k * ∂²ξ*A(x - cᵍ * t, y) * ûˢ(z)

stokes*drift = StokesDrift(; ∂z*uˢ, ∂t*uˢ, ∂y*uˢ, ∂t*wˢ, ∂x*wˢ, ∂y_wˢ)

# 出力

StokesDrift{Nothing}: ├── ∂x*vˢ: zerofunction ├── ∂x*wˢ: ∂x*wˢ ├── ∂y*uˢ: ∂y*uˢ ├── ∂y*wˢ: ∂y*wˢ ├── ∂z*uˢ: ∂z*uˢ ├── ∂z*vˢ: zerofunction ├── ∂t*uˢ: ∂t*uˢ ├── ∂t*vˢ: zerofunction └── ∂t*wˢ: ∂t_wˢ ```
