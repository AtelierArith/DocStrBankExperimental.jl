```
uniform2D(ρ::Float64, p::Pattern2D, field_x::Float64, field_y::Float64)
```

ランダムに配置され回転した2Dパターンの座標配列を作成します。

# 引数

  * `ρ::Float64`: パターン密度（平方ミクロンあたりのパターン数）
  * `p::Pattern2D`: 複製するパターン
  * `field_x::Float64`: フィールドの幅（ミクロン単位）
  * `field_y::Float64`: フィールドの高さ（ミクロン単位）

# 戻り値

  * `Tuple{Vector{Float64}, Vector{Float64}}`: ミクロン単位の(x, y)座標

# 例

```julia
# ランダムに配置されたNmer2Dパターンの座標を生成
nmer = Nmer2D(; n=6, d=0.2)
x, y = uniform2D(1.0, nmer, 10.0, 10.0)
```
