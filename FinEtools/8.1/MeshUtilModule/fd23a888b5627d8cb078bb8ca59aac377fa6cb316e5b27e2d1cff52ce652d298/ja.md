```
logspace(start::T, stop::T, N::Int)  where {T<:Number}
```

対数空間を生成します。

`start` と `stop` の間に `N` 個の数値の対数列を生成します（すなわち、対数空間内で均等な間隔の数値の列）。

# 例

```
julia> logspace(2.0, 3.0, 5)                                                             
5-element Array{Float64,1}:                                                              
  100.0
  177.82794100389228   
  316.2277660168379      
  562.341325190349  
 1000.0    
```
