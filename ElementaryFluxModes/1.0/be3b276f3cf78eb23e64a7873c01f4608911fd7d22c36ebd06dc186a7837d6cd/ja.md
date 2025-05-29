```julia
get_ofms(
    N::Matrix{Float64},
    fixed_fluxes::Vector{Int64},
    flux_values::Vector{Float64}
) -> Any

```

剪定された最適解の最適フラックスモードを計算します。引数:

  * `N`: 剪定されたモデルのストイキオメトリック行列
  * `fixed_fluxes`: 固定フラックスのインデックス
  * `flux_values`: 固定フラックスの最適値

出力: OFMの行列、各列は異なるOFMであり、行は入力`N`の反応インデックスに対応します。
