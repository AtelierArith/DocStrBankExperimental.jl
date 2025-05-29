```
uniform3D(ρ::Float64, p::Pattern3D, field_x::Float64, field_y::Float64; 
         zrange::Vector{Float64}=[-1.0, 1.0])
```

ランダムに配置され回転した3Dパターンの座標配列を作成します。

# 引数

  * `ρ::Float64`: パターン密度（平方ミクロンあたりのパターン数）
  * `p::Pattern3D`: 複製するパターン
  * `field_x::Float64`: フィールドの幅（ミクロン単位）
  * `field_y::Float64`: フィールドの高さ（ミクロン単位）
  * `zrange::Vector{Float64}=[-1.0, 1.0]`: [min*z, max*z] の範囲（ミクロン単位）

# 戻り値

  * `Tuple{Vector{Float64}, Vector{Float64}, Vector{Float64}}`: (x, y, z) 座標

# 例

```julia
# ランダムに配置されたNmer3Dパターンの座標を生成
nmer = Nmer3D(; n=6, d=0.2)
x, y, z = uniform3D(1.0, nmer, 10.0, 10.0; zrange=[-2.0, 2.0])
```
