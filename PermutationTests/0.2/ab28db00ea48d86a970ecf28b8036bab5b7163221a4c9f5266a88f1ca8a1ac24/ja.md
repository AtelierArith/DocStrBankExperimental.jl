```julia
function statistic(x::UniData, y::UniData, stat::Sum; 
                kwargs...)  
```

入力データベクトル `y` の要素の合計。

一般的に一標本 *t* 検定統計量に相当します。詳細は [Statistic](@ref) を参照してください。

`x` は [`membership(::OneSampStatistic)`](@ref) ベクトルです。
