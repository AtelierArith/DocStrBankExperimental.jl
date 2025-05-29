```
Volume_Source
```

等方的体積ソースとその特性を定義するために使用される構造体。

# 必須フィールド

  * `name::String` : Volume_Source 構造体の名前（または識別子）。
  * `particle::Particle` : 放出される粒子のタイプ。
  * `energy_group::Int64` : 粒子が放出されるエネルギーグループのインデックス。
  * `boundaries::Vector{Float64}` : 各軸に沿ったソースの境界 [cm 単位]。

# オプションフィールド - デフォルト値あり

  * `intensity::Float64=1.0` : 強度 [# 粒子/cmᴺ、ここで N は幾何学的次元]。
