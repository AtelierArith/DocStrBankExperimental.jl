`Glacier2D`オブジェクトを指定されたパラメータで構築します。デフォルトのパラメータも含まれます。

```
Glacier2D(;
    rgi_id::Union{String, Nothing} = nothing,
    name::String = "",
    climate::Union{Climate2D, Nothing} = nothing,
    H₀::Union{Matrix{F}, Nothing} = nothing,
    H_glathida::Union{Matrix{F}, Nothing} = nothing,
    S::Union{Matrix{F}, Nothing} = nothing,
    B::Union{Matrix{F}, Nothing} = nothing,
    V::Union{Matrix{F}, Nothing} = nothing,
    Vx::Union{Matrix{F}, Nothing} = nothing,
    Vy::Union{Matrix{F}, Nothing} = nothing,
    A::Union{F, Nothing} = nothing,
    C::Union{F, Nothing} = nothing,
    n::Union{F, Nothing} = nothing,
    slope::Union{Matrix{F}, Nothing} = nothing,
    dist_border::Union{Matrix{F}, Nothing} = nothing,
    Coords::Union{Dict{String, Vector{Float64}}, Nothing} = nothing,
    Δx::Union{F, Nothing} = nothing,
    Δy::Union{F, Nothing} = nothing,
    nx::Union{I, Nothing} = nothing,
    ny::Union{I, Nothing} = nothing,
    cenlon::Union{F, Nothing} = nothing,
    cenlat::Union{F, Nothing} = nothing,
    params_projection::Dict{String, Float64} = Dict{String, Float64}(),
    thicknessData::Union{ThicknessData, Nothing} = nothing,
    velocityData::Union{SurfaceVelocityData, Nothing} = nothing,
) where {F <: AbstractFloat, I <: Integer}
```

# 引数

  * `rgi_id::String`: 氷河のRGI識別子。
  * `name::String`: 利用可能な場合の氷河の名前。
  * `climate::Union{Climate2D, Nothing}`: 氷河に関連する気候データ。
  * `H₀::Union{Matrix{F}, Nothing}`: 初期氷厚マトリックス。
  * `H_glathida::Matrix{F}`: GLATHIDAからの氷厚マトリックス。
  * `S::Matrix{F}`: 表面標高マトリックス。
  * `B::Matrix{F}`: 床標高マトリックス。
  * `V::Union{Matrix{F}, Nothing}`: 氷の速度の大きさマトリックス。
  * `Vx::Union{Matrix{F}, Nothing}`: x方向の氷の速度マトリックス。
  * `Vy::Union{Matrix{F}, Nothing}`: y方向の氷の速度マトリックス。
  * `A::Union{F, Nothing}`: 流動法パラメータ。
  * `C::Union{F, Nothing}`: スライディング法パラメータ。
  * `n::Union{F, Nothing}`: 流動法指数。
  * `slope::Union{Matrix{F}, Nothing}`: 傾斜マトリックス。
  * `dist_border::Union{Matrix{F}, Nothing}`: 境界までの距離マトリックス。
  * `Coords::Union{Dict{String, Vector{Float64}}, Nothing}`: "lon"と"lat"のキーを持つ座標辞書。
  * `Δx::F`: x方向のグリッド間隔。
  * `Δy::F`: y方向のグリッド間隔。
  * `nx::I`: x方向のグリッドポイント数。
  * `ny::I`: y方向のグリッドポイント数。
  * `cenlon::Union{F, Nothing}`: 氷河の中央経度。
  * `cenlat::Union{F, Nothing}`: 氷河の中央緯度。
  * `params_projection::Dict{String, Float64}`: 地域グリッドをグローバルWGS84座標にマッピングするための投影パラメータ。
  * `thicknessData::Union{ThicknessData, Nothing}`: 参照値を格納するために使用される厚さデータ構造。
  * `velocityData::Union{SurfaceVelocityData, Nothing}`: 参照値を格納するために使用される表面速度データ構造。

# 戻り値

  * 指定されたパラメータを持つ`Glacier2D`オブジェクト。
