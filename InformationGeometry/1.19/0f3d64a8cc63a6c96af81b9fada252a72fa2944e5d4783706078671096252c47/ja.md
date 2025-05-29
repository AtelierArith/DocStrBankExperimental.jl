```
ApproxInRegion(sol::AbstractODESolution, p::AbstractVector{<:Number}) -> Bool
```

2D ODESolutionの基準点によって定義された多角形内に点が存在するかどうかを非常に高速に近似的にテストします。特に、信頼境界が明示的に計算された後の仮説検定に適しています。
