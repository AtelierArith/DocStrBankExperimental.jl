衛生技術を表します。 `Source` と `Sink` はエイリアスです。

次のフィールドがあります：

  * `inputs::Vector{Santiago.Product}`
  * `outputs::Vector{Santiago.Product}`
  * `name::String`
  * `functional_group::Symbol`
  * `appscore::Array{Float64}`: 特定のケースに対する適合性スコア。
  * `n_inputs::Int64`
  * `transC::Dict{String, Dict{Santiago.Product, Float64}}`: 移転係数
  * `transC_reliability::Dict{String, Float64}`: 移転係数に関連する不確実性因子
