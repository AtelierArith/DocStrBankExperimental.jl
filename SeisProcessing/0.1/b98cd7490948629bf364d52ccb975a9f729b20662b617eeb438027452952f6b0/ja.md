SeisHypEvents(; <キーワード引数>)

双曲線イベントからなる二次元データを生成します。

# 引数

  * `ot::Real=0.0`: 時間軸の最初のサンプル（秒単位）。
  * `dt::Real=0.004`: 時間サンプリング間隔（秒単位）。
  * `nt::Int=301`: 時間サンプルの数。
  * `ox::Real=-1000.0`: 空間次元の最初のサンプル（メートル単位）。
  * `dx::Real=20.0`: 空間次元のサンプル間隔（メートル単位）。
  * `nx::Int=101`: 空間次元のサンプル数。
  * `tau::Vector{Real}=[0.2, 0.6, 0.9]`: 各イベントの切片到達時間。
  * `vel::Vector{Real}=[1500.0, 2000.0, 3000.0]`: rms速度（m/s）。
  * `apex::Vector{Real}=[0.0, 0.0, 0.0]`: 頂点シフト（メートル単位）。
  * `amp::Vector{Real}=[1.0, -1.0, 1.0]`: 各イベントの振幅。
  * `wavelet::AbstractString="ricker"`: イベントをモデル化するために使用されるウェーブレット。
  * `f0::Vector{Real}=[20.0]`: 各イベントのウェーブレットの中心周波数。

# 出力

  * `d::Array{Real, 2}`: 双曲線イベントからなる二次元データ。

# 例

```julia
julia> using SeisPlot
julia> d = SeisHypEvents(); SeisPlotTX(d);
julia> d = SeisHypEvents(apex=[100, 200, -300], f0=[30, 20, 15]);
SeisPlotTX(d);
```
