Lennard-Jones 力場のデータ構造。

# 属性

  * `name::String`: 力場の名前; ファイル名に対応
  * `pure_σ::Dict{Symbol, Float64}`: X-X 相互作用の Lennard-Jones σ を返す辞書。ここで X は原子です。（単位: オングストローム）
  * `pure_ϵ::Dict{Symbol, Float64}`: X-X 相互作用の Lennard-Jones ϵ を返す辞書。ここで X は原子です。（単位: K）
  * `σ²::Dict{Symbol, Dict{Symbol, Float64}}`: クロス相互作用のための Lennard-Jones σ²（単位: オングストローム²）。使用例は `sigmas_squared[:He][:C]`
  * `ϵ::Dict{Symbol, Dict{Symbol, Float64}}`: クロス相互作用のための Lennard-Jones ϵ（単位: K）。使用例は `epsilons[:He][:C]`
  * `r²_cutoff::Float64`: ポテンシャルエネルギーをゼロと定義するカットオフ半径の二乗（単位: オングストローム²）。計算を高速化するために σ² を保存します。計算には σ ではなく σ² が関与します。
