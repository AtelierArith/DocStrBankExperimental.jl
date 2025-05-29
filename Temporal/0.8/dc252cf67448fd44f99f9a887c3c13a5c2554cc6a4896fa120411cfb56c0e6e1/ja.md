```
acf(x::TS,maxlag::Int=15;lags::AbstractArray{Int,1}=0:maxlag)
acf(x::Vector{T},maxlag::Int=15;lags::AbstractArray{Int,1}=0:maxlag)::Vector{Float64}where{T<:Number}
acf(x::Matrix{T},maxlag::Int=15;lags::AbstractVector{Int}=0:maxlag)::Matrix{Float64}where{T<:Number}
```

時系列の自己相関関数を計算します。

出力は、入力時系列 `x` と同じ列数を持ち、自己相関関数に使用されるラグの数に等しい行数を持つ行列になります。

...

# 引数

  * `x::TS`: 自己相関を計算する列を含む時系列オブジェクト配列。
  * `maxlag::Int=15`: 自己相関系列の最大ラグ。

オプション引数:

  * `lags::AbstractArray{Int,1}=0:maxlag`: 使用するラグの明示的に指定されたリスト（`maxlag` の使用を上書きします）。

...
