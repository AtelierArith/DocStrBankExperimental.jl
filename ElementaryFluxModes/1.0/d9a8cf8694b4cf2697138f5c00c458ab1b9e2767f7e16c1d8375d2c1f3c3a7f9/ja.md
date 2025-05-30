```julia
differentiate_efm(
    EFMs::Vector{Dict{String, Float64}},
    parameters::Vector{FastDifferentiation.Node},
    rid_pid::Dict{String, FastDifferentiation.Node},
    parameter_values::Dict{Symbol, Float64},
    rid_gcounts::Dict{String, Dict{String, Float64}},
    capacity::Vector{Tuple{String, Vector{String}, Float64}},
    gene_product_molar_masses::Dict{String, Float64},
    optimizer
) -> Any

```

モデルパラメータの変化に対するEFMの使用を、ラグランジアンの暗黙的微分を用いて微分します。最適解における各EFMの使用割合を次の線形計画問題に変換できます：     最大化     ∑xᵢ     制約条件   Dx = 1 ここでDは各酵素プールにおける各EFMに関連するコスト行列です。次に、このLPのラグランジアンを微分して、パラメータによるxの微分を計算します。

引数：

  * 'EFMs': EFMの辞書のベクトル
  * 'parameters': モデルパラメータのベクトル
  * `rid_pid`: 反応ID => パラメータIDの辞書
  * `parameter_values`: パラメータシンボル => 浮動小数点値の辞書
  * `rid_gcounts`: 反応ID => 遺伝子産物カウントの辞書
  * `capacity`: 酵素制約モデルの酵素容量制限
  * `gene_product_molar_masses`: 遺伝子産物遺伝子*産物*モル質量の辞書

出力：パラメータjに対するEFM iの微分の行列Aᵢⱼ：d(EFMᵢ)/d(pⱼ)
