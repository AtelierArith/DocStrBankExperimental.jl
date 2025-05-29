```
agg_time(A::AbstractArray{T,3}, by::Vector; parallel=true, progress=false, 
    fun=mean) where {T<:Real}
agg_time(A::AbstractArray{T,3}; fact::Int=2, parallel=true, progress=false, 
  fun=mean) where {T<:Real}
```
