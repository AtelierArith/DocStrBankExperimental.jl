```
Surface_Source
```

方向性境界ソースとその特性を定義するために使用される構造体。

# 必須フィールド

  * `name::String` : Surface_Source 構造体の名前（または識別子）。
  * `particle::Particle` : 放出される粒子のタイプ。
  * `energy_group::Int64` : 粒子が放出されるエネルギーグループのインデックス。
  * `direction::Vector{Float64}` : 方向コサイン。
  * `location::String` : ソースが位置する境界。
  * `boundaries::Vector{Float64}` : 各軸に沿ったソースの境界 [cm単位]。

# オプションフィールド - デフォルト値あり

  * `intensity::Float64=1.0` : 強度 [# 粒子/cm⁽ᴺ⁻¹⁾、ここで N は幾何学的次元]。
