```
filename = μVT_output_filename(xtal, molecule_templates, temperature, 
                               pressures, ljff, n_burn_cycles, 
                               n_sample_cycles; comment="", extension=".jld2")
```

これは、[μVT_sim](@ref)で使用されるファイル命名規則を確立する関数です。

# 引数

  * `xtal::Crystal`: 吸着シミュレーションに使用される多孔質結晶
  * `molecule_templates::Array{Molecule, 1}`: 吸着シミュレーションに使用される吸着分子のテンプレート
  * `temperature::Float64`: 吸着相と多孔質材料の平衡にあるバルクガス相の温度。単位: ケルビン (K)
  * `pressures::Array{Float64, 1}`: 吸着相と多孔質材料の平衡にあるバルクガス相の部分圧。単位: バール
  * `ljff::LJForceField`: 吸着シミュレーションに使用される分子モデル
  * `n_burn_cycles::Int`: サンプリング前にシステムが平衡に達するのを許可するサイクル数
  * `n_sample_cycles::Int`: サンプリングに使用されるサイクル数
  * `comment::String=""`: ファイル名に含める備考
  * `extension::String=".jld2"`: ファイル拡張子

# 戻り値

  * `filename::String`: 特定の `.jld2` シミュレーションファイルの名前
