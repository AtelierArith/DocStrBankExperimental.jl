```
PencilGrids(length, resol)
PencilGrids(length_tuple, resol_tuple::Tuple{Int, Int, Int})
```

シミュレーションで使用されるグリッドを含む構造体

各グリッドは `PencilArray` であり、マルチプロセス FFT を可能にします。これはかなりのオーバーヘッドを伴うため、マルチノード環境で実行する場合にのみ有用です。

# フィールド

  * `x::Array{Float64, 3}`: x 位置の配列
  * `y::Array{Float64, 3}`: y 位置の配列
  * `z::Array{Float64, 3}`: z 位置の配列
  * `kx::Array{Float64, 3}`: x フーリエモードの配列
  * `ky::Array{Float64, 3}`: y フーリエモードの配列
  * `kz::Array{Float64, 3}`: z フーリエモードの配列
  * `k::Any`: フーリエ空間位置配列
  * `rkx::Array{Float64, 3}`: `rfft` 用の x フーリエモードの配列
  * `rky::Array{Float64, 3}`: `rfft` 用の y フーリエモードの配列
  * `rkz::Array{Float64, 3}`: `rfft` 用の z フーリエモードの配列
  * `rk::Any`: `rfft` 用のフーリエ空間位置配列
  * `ψx::Any`: ψ フィールド
  * `ψk::Any`: フーリエ空間の ψ フィールド
  * `ρx::Any`: 密度フィールド ρ
  * `ρk::Any`: フーリエ空間の密度フィールド ρ
  * `Φx::Any`: 重力ポテンシャルフィールド Φ
  * `Φk::Any`: フーリエ空間の重力ポテンシャルフィールド Φ
  * `fft_plan::Any`: 複素数から複素数への変換のための FFT プラン
  * `rfft_plan::Any`: 実数から複素数への変換のための FFT プラン
  * `k_vanish_indices::Vector{CartesianIndex{3}}`: k==0.0 となるインデックス
  * `rk_vanish_indices::Any`: rk==0.0 となるインデックス
  * `MPI_COMM::Any`: MPI コミュニケーター

# 例

長さ `length` と解像度 `resol` の空のグリッドを作成します。 `PencilFFTs` を使用して `PencilArrays` を作成します。

```jldoctest
julia> using UltraDark

julia> len = 1;

julia> resol = 16;

julia> PencilGrids(len, resol);

```

解像度 `resol[1]`x`resol[2]`x`resol[3]` の空の `length[1]`x`length[2]`x`length[3]` グリッドを作成します。

```jldoctest
julia> using UltraDark

julia> PencilGrids((1.0, 1.0, 0.5), (64, 64, 32));

```
