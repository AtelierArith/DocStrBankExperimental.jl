```julia
function statistic(x::IntVec, y::UniData, stat::Group1Total_IS; 
                kwargs...)            
```

グループ1の観測値の合計。

独立したサンプルの方向性テストに対するスチューデントの *t* 検定統計量に相当します。詳細は [Statistic](@ref) を参照してください。

引数 `x` と `y` について、また例については、上記の `AnovaF_IS` の [`statistic`](@ref) メソッドを参照してください。
