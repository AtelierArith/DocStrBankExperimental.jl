可変構造体は2D氷河を表します。すべてのフィールドは、デフォルト値として`nothing`を提供することで空にすることができます。

/!\ 警告 /!\ `Glacier`オブジェクトは手動で構築するべきではなく、`initialize_glaciers`関数を通じて構築するべきです。

`Glacier2D{F <: AbstractFloat, I <: Integer}`

# フィールド

  * `rgi_id::String`: 氷河のRGI（Randolph Glacier Inventory）識別子。
  * `name::String`: 利用可能な場合の氷河の名前。
  * `climate::Union{Climate2D, Nothing}`: 氷河に関連する気候データ。
  * `H₀::Union{Matrix{F}, Nothing}`: 初期氷厚行列。
  * `H_glathida::Matrix{F}`: GLATHIDAデータセットからの氷厚行列。
  * `S::Matrix{F}`: 表面標高行列。
  * `B::Matrix{F}`: 基盤岩標高行列。
  * `V::Union{Matrix{F}, Nothing}`: 氷の速度の大きさ行列。
  * `Vx::Union{Matrix{F}, Nothing}`: x方向の氷の速度行列。
  * `Vy::Union{Matrix{F}, Nothing}`: y方向の氷の速度行列。
  * `A::Union{F, Nothing}`: 流動法パラメータ。
  * `C::Union{F, Nothing}`: スライディング法パラメータ。
  * `n::Union{F, Nothing}`: 流動法指数。
  * `slope::Union{Matrix{F}, Nothing}`: 表面傾斜行列。
  * `dist_border::Union{Matrix{F}, Nothing}`: 氷河の境界までの距離行列。
  * `Coords::Union{Dict{String, Vector{Float64}}, Nothing}`: 座標名をキーとし、座標のベクトルを値とする座標辞書。
  * `Δx::F`: x方向のグリッド間隔。
  * `Δy::F`: y方向のグリッド間隔。
  * `nx::I`: x方向のグリッドポイントの数。
  * `ny::I`: y方向のグリッドポイントの数。
  * `cenlon::Union{F, Nothing}`: 氷河中心の経度。
  * `cenlat::Union{F, Nothing}`: 氷河中心の緯度。
  * `params_projection::Dict{String, Float64}`: 地域グリッドを全球WGS84座標にマッピングするための投影パラメータ。
  * `thicknessData::Union{ThicknessData, Nothing}`: 参照値を格納するために使用される厚さデータ構造。
  * `velocityData::Union{SurfaceVelocityData, Nothing}`: 参照値を格納するために使用される表面速度データ構造。
