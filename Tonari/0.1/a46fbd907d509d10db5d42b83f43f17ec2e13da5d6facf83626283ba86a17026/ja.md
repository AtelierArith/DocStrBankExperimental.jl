```
fill_gaps(rng::AbstractRNG, t::Vector{Float64}, x::Vector{Float64}, σₓ = nothing; randomise_values::Bool = true, poisson::Bool = true)
```

時間系列データのギャップを線形補間で埋めます。`randomise_values = true`の場合、補間された値はデータの平均と標準偏差に基づく正規分布から抽出されます。`poisson = true`の場合、補間された値はデータの平均に基づくポアソン分布から抽出されます。

# 引数

  * `rng::AbstractRNG`: 擬似乱数生成器
  * `t::Vector{Float64}`: 時間配列
  * `x::Vector{Float64}`: データ配列
  * `σₓ`::Vector{Float64}: データ配列の標準偏差（オプション）
  * `randomise_values::Bool`: 補間された値をランダム化するかどうか
  * `poisson::Bool`: 補間された値にポアソン分布を使用するかどうか、これはデータがカウント/dtであることを前提としています
