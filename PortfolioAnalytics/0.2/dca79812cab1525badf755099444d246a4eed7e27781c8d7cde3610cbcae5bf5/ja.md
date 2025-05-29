```
cumulative_return(R::TSFrame; geometric::Bool=true, verbose=false)
```

資産の累積リターンを計算します。

# 引数:

  * `R::TSFrame`: 資産リターンのTSFrameオブジェクトの列
  * `geometric::Bool=true`: trueの場合、幾何学的リターンを計算します
  * `verbose=false`: trueの場合、データ履歴の累積資産リターンのTSFrameオブジェクトを返します

# 例

```julia
julia> cumulative_return(returns)
3-element Named Vector{Float64}
Cumulative Return  │
───────────────────┼─────────
TSLA               │ 0.497577
NFLX               │ 0.114123
MSFT               │ 0.512094

julia> cumulative_return(returns, verbose=true)
12×3 TSFrame with Date Index
 Index       TSLA      NFLX      MSFT    
 Date        Float64   Float64   Float64 
─────────────────────────────────────────
 2021-01-31  1.12452   0.984576  1.04289
 2021-02-28  0.957232  0.996523  1.04478
 2021-03-31  0.946518  0.964733  1.06002
 2021-04-30  1.00536   0.949587  1.1338
 2021-05-31  0.885979  0.929873  1.12256
 2021-06-30  0.963183  0.976846  1.21797
 2021-07-31  0.973812  0.957169  1.28095
 2021-08-31  1.0426    1.05263   1.35725
 2021-09-30  1.09893   1.12873   1.26751
 2021-10-31  1.57865   1.27663   1.49096
 2021-11-30  1.62223   1.1871    1.48633
 2021-12-31  1.49758   1.11412   1.51209

 julia> cumulative_return(returns, geometric=false)
3-element Named Vector{Float64}
Cumulative Return  │
───────────────────┼─────────
TSLA               │ 0.518126
NFLX               │ 0.130176
MSFT               │ 0.439646
```
