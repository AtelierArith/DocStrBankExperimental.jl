```
result = henry_coefficient(crystal, molecule, temperature, ljforcefield,
                            insertions_per_volume=200, verbose=true, ewald_precision=1e-6,
                            autosave=true)
```

結晶中の分子のヘンリー係数 Kₕ を計算するために粒子挿入を行います。また、自由に、吸着の熱と吸着のアンサンブル平均エネルギーも計算されます。ヘンリー係数は無限希釈（低被覆）での吸着のモデルです: ⟨N⟩ = Kₕ P、ここで P は圧力、Kₕ はヘンリー係数です。

Kₕ = β ⟨e^{-β U}⟩、ここで平均は結晶内の分子の位置と向きにわたります。

# 引数

  * `crystal::Crystal`: 吸着をシミュレートしようとする多孔質結晶
  * `molecule::Molecule`: 吸着分子
  * `temperature::Float64`: 吸着相と多孔質材料内の平衡にあるバルクガス相の温度。単位: ケルビン (K)
  * `ljforcefield::LJForceField`: 吸着物質-吸着物質および吸着物質-ホストのファンデルワールス相互作用のエネルギーを記述するために使用される分子モデル。
  * `insertions_per_volume::Int`: 平均を計算するために行うウィドム挿入の数、単位セル体積あたり (Å³)
  * `verbose::Bool`: シミュレーション中に情報を印刷するかどうか。
  * `ewald_precision::Float64`: エヴァルド和のための望ましい精度; 逆空間での複製因子を決定するために使用されます。
  * `autosave::Bool`: 結果ファイルを .jld2 として rc[:paths][:simulations] に保存
  * `filename_comment::AbstractString`: 保存されたファイルの名前に追加されるオプションのコメント。

# 戻り値

  * `result::Dict{String, Float64}`: ヘンリー係数シミュレーションからのすべての結果を含む辞書
