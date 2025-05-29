漸近分散推定量

aVar(k::AVarEstimator, m::AbstractMatrix{T}; demean::Bool=true, dims::Int=1, means::Union{Nothing, AbstractArray}=nothing, prewhite::Bool=false, scale=true)

## 引数

```
- k::AVarEstimator 
- `demean=false`: データを平均化するかどうか。    
- `prewhite=false`: データを事前にホワイトニングするべきか。`HAC`推定量に関連。
```
