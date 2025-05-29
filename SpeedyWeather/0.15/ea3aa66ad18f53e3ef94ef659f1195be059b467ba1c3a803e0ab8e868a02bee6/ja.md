Geometry構造体を構築し、iso-latitudeグリッド`<:AbstractGrid`および垂直レベルを記述するパラメータと配列を含めます。次のフィールドを計算するために`SpectralGrid`を渡します。

  * `spectral_grid::SpeedyWeather.SpectralGrid`: スペクトルおよびグリッド解像度を定義するSpectralGrid
  * `nlat_half::Int64`: グリッドの解像度パラメータnlat_half、1つの半球の緯度の数（赤道を含む）
  * `nlon_max::Int64`: 最大の経度の数（赤道付近）
  * `nlat::Int64`: 緯度リングの数
  * `nlayers::Int64`: 垂直レベルの数
  * `npoints::Int64`: 水平グリッドポイントの総数
  * `radius::Any`: 惑星の半径 [m]
  * `lond::Any`: 経度の配列（度単位、0...360˚）、非完全グリッドの場合は空
  * `latd::Any`: 緯度の配列（度単位、90˚...-90˚）
  * `lat::Any`: 緯度の配列（ラジアン単位、π...-π）
  * `colat::Any`: コラティチュードの配列（ラジアン単位、0...π）
  * `londs::Any`: 各グリッドポイントの経度（0˚...360˚）、リング順
  * `latds::Any`: 各グリッドポイントの緯度（-90˚...90˚）、リング順
  * `lons::Any`: 各グリッドポイントの経度（0...2π）、リング順
  * `lats::Any`: 各グリッドポイントの緯度（-π/2...π/2）、リング順
  * `sinlat::Any`: 緯度のsin
  * `coslat::Any`: 緯度のcos
  * `coslat⁻¹::Any`: = 1/cos(lat)
  * `coslat²::Any`: = cos²(lat)
  * `coslat⁻²::Any`: # = 1/cos²(lat)
  * `σ_levels_half::Any`: 半レベルでのσ、σ_k+1/2
  * `σ_levels_full::Any`: 完全レベルでのσ、σₖ
  * `σ_levels_thick::Any`: σレベルの厚さ、σₖ₊₁ - σₖ
  * `ln_σ_levels_full::Any`: 完全レベルでのσの対数、表面（σ=1）を最後の要素として含む
  * `full_to_half_interpolation::Any`: 完全レベルから半レベルへの補間
