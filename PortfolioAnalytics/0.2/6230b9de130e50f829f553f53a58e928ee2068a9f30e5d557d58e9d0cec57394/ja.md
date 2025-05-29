```
portfolio_return(price::TSFrame, weights::Vector{<:Number}; period::Int=1, method::String="simple", colname::String="PORT")
```

`ポートフォリオリターン`を`資産価格`と与えられた`ウェイト`から計算します。

# 引数:

  * `price::TSFrame`: 資産価格のTSFrameオブジェクトの列
  * `weights::Vector{<:Number}`: 資産のウェイト
  * `period::Int=1`: リターン期間
  * `method::String="simple"`: リターン方法、利用可能な方法; `"simple"` と `"log"`
  * `colname::String="PORT"`: ポートフォリオリターンの列の名前

# 例

```julia
julia> preturns = portfolio_return(prices_ts, weights)
12×1 TSFrame with Date Index
 Index       PORT        
 Date        Float64?    
─────────────────────────
 2021-01-31   0.0522176
 2021-02-28  -0.0542905
 2021-03-31  -0.0143197
 2021-04-30   0.0325056
 2021-05-31  -0.0577836
 2021-06-30   0.0720602
 2021-07-31   0.00669974
 2021-08-31   0.0800613
 2021-09-30   0.037306
 2021-10-31   0.262282
 2021-11-30  -0.017631
 2021-12-31  -0.0518583


 julia> log_preturns = portfolio_return(prices_ts, weights, method = "log")
 12×1 TSFrame with Date Index
  Index       PORT        
  Date        Float64?    
 ─────────────────────────
  2021-01-31   0.0491251
  2021-02-28  -0.0592409
  2021-03-31  -0.014574
  2021-04-30   0.0312505
  2021-05-31  -0.060946
  2021-06-30   0.0694468
  2021-07-31   0.00633473
  2021-08-31   0.0769004
  2021-09-30   0.0352874
  2021-10-31   0.226617
  2021-11-30  -0.0188137
  2021-12-31  -0.0539213
```

# 注意:

  * 関数からの`missing`は自動的に削除されます。
