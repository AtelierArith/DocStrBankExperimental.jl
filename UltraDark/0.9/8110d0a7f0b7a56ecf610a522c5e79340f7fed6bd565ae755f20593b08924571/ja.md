```julia
struct Grids <: UltraDark.AbstractGrids
```

```
Grids(length, resol::Int)
Grids(length_tuple, resol_tuple::Tuple{Int, Int, Int})
```

シミュレーションで使用されるグリッドを含む構造体

# フィールド

  * `x::Array{Float64, 3}`: x位置の配列
  * `y::Array{Float64, 3}`: y位置の配列
  * `z::Array{Float64, 3}`: z位置の配列
  * `kx::Array{Float64, 3}`: xフーリエモードの配列
  * `ky::Array{Float64, 3}`: yフーリエモードの配列
  * `kz::Array{Float64, 3}`: zフーリエモードの配列
  * `k::Array{Float64, 3}`: フーリエ空間位置配列
  * `rkx::Array{Float64, 3}`: `rfft`で使用するためのxフーリエモードの配列
  * `rky::Array{Float64, 3}`: `rfft`で使用するためのyフーリエモードの配列
  * `rkz::Array{Float64, 3}`: `rfft`で使用するためのzフーリエモードの配列
  * `rk::Array{Float64, 3}`: `rfft`で使用するためのフーリエ空間位置配列
  * `ψx::Array{ComplexF64, 3}`: ψフィールド
  * `ψk::Array{ComplexF64, 3}`: フーリエ空間のψフィールド
  * `ρx::Array{Float64, 3}`: 密度フィールドρ
  * `ρk::Array{ComplexF64, 3}`: フーリエ空間の密度フィールドρ
  * `Φx::Array{Float64, 3}`: 重力ポテンシャルフィールドΦ
  * `Φk::Array{ComplexF64, 3}`: フーリエ空間の重力ポテンシャルフィールドΦ
  * `fft_plan::Any`: 複素数から複素数への変換のためのFFTプラン
  * `rfft_plan::Any`: 実数から複素数への変換のためのFFTプラン
  * `k_vanish_indices::Vector{CartesianIndex{3}}`: k==0.0となるインデックス
  * `rk_vanish_indices::Any`: rk==0.0となるインデックス

# 例

長さ`length`と解像度`resol`の空のグリッドを作成します

```jldoctest
julia> using UltraDark

julia> length = 1;

julia> resol = 16;

julia> Grids(length, resol);

julia> size(ans.ψx)
(16, 16, 16)
```

解像度`resol[1]`x`resol[2]`x`resol[3]`の空の`length[1]`x`length[2]`x`length[3]`グリッドを作成します。

```jldoctest
julia> using UltraDark

julia> Grids((1.0, 1.0, 0.5), (64, 64, 32));

julia> size(ans.ψx)
(64, 64, 32)
```
