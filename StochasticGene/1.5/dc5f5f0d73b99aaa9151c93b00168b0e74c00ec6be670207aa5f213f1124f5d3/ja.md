```
datapdf(data)
```

正規化されたRNAヒストグラムデータを1つのベクターとして返します。

# 引数

  * `data::AbstractRNAData{Array{Float64,1}}`: RNAヒストグラムデータ。
  * `data::RNAOnOffData`: RNA On/Offデータ。
  * `data::AbstractTraceHistogramData`: トレースヒストグラムデータ。
  * `data::AbstractRNAData{Array{Array,1}}`: ネストされた配列を持つRNAヒストグラムデータ。
  * `data::RNADwellTimeData`: RNA滞留時間データ。

# 説明

この関数はRNAヒストグラムデータを正規化し、1つのベクターとして返します。RNAヒストグラムデータ、RNA On/Offデータ、トレースヒストグラムデータ、RNA滞留時間データなど、さまざまなタイプのRNAデータをサポートしています。

# メソッド

  * `datapdf(data::AbstractRNAData{Array{Float64,1}})`: RNAヒストグラムデータを正規化して返します。
  * `datapdf(data::RNAOnOffData)`: RNA On/Offデータを正規化して返します。
  * `datapdf(data::AbstractTraceHistogramData)`: トレースヒストグラムデータを正規化して返します。
  * `datapdf(data::AbstractRNAData{Array{Array,1}})`: ネストされた配列を持つRNAヒストグラムデータを正規化して返します。
  * `datapdf(data::RNADwellTimeData)`: RNA滞留時間データを正規化して返します。

# 返り値

  * `Vector{Float64}`: 1つのベクターとして正規化されたRNAヒストグラムデータ。
