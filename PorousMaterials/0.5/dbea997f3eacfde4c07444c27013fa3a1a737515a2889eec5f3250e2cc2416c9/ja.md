```
dataframe = isotherm_sim_results_to_dataframe(desired_props, xtal,
                                              molecule, temperature,
                                              pressures, ljff,
                                              n_burn_cycles, n_sample_cycles;
                                              where_are_jld_files=nothing)`
```

[`μVT_sim`](@ref) から自動保存された `.jld2` 結果出力ファイルを `DataFrame` に変換します。 `DataFrame` の各行は、吸着等温線の圧力に対応しています。 `desired_props` は結果から取得したいプロパティの配列です。要求された出力ファイルを特定するために、この関数は [`μVT_output_filename`](@ref) を呼び出してファイル名を取得します。

# 引数

  * `desired_props::Array{String, 1}`: `.jld2` ファイルから取得するプロパティの名前を含む配列
  * `xtal::Crystal`: 多孔質結晶
  * `molecule::Array{Molecule{Cart}, 1}`: 吸着分子
  * `temperature::Float64`: シミュレーションの温度、単位: ケルビン (K)
  * `pressures::Array{Array{Float64, 1}, 1}`: 吸着等温線シミュレーションの圧力、単位: バール
  * `ljff::LJForceField`: 分子間のファン・デル・ワールス相互作用を記述するためにシミュレーションで使用される分子モデル
  * `n_burn_cycles::Int64`: このシミュレーションで使用されるバーナーサイクルの数
  * `n_sample_cycles::Int64`: シミュレーションで使用されるサンプルサイクルの数
  * `where_are_jld_files::Union{String, Nothing}=nothing`: シミュレーションファイルの場所。デフォルトは `PorousMaterials.rc[:paths][:simulations]`。
  * `comment::String=""`: 出力ファイル名に追加されるコメント

# 戻り値

  * `dataframe::DataFrame`: 吸着等温線に沿ったシミュレーションデータを含む `DataFrame` で、列は指定されたプロパティ用です

# 注意

圧力の範囲を使用して、`DataFrame` に含めるシミュレーションファイルのバッチを選択できます。

# 例

```julia
xtal = Crystal("SBMOF-1.cif")
molecule = Molecule("Xe")
ljff = LJForceField("UFF"; mixing_rules="Lorentz-Berthelot")
temperature = 298.0 # K
pressures = 10 .^ range(-2; stop=2, length=15)

dataframe = isotherm_sim_results_to_dataframe(
    ["pressure (bar)", "⟨N⟩ (mmol/g)"],
    xtal,
    molecule,
    temperature,
    pressures,
    ljff,
    10000,
    10000
)
dataframe[Symbol("pressure (bar)")] # 圧力
dataframe[Symbol("⟨N⟩ (mmol/g)")] # 対応する圧力での吸着
```
