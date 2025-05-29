```
MedianFilter([T=Float64,] window_length) where T <: Real
```

Construct a stateful running median filter, taking values of type `T`. 

Manipulate with [`grow!`](@ref), [`roll!`](@ref), [`shrink!`](@ref), [`reset!`](@ref).  Query with [`median`](@ref), [`length`](@ref), [`window_length`](@ref), [`isfull`](@ref). 

# Examples

```jldoctest
julia> mf = MedianFilter(Int64, 2)
MedianFilter{Int64}(MutableBinaryHeap(), MutableBinaryHeap(), Tuple{FastRunningMedian.ValueLocation, Int64}[], 0, 0)

julia> grow!(mf, 1); median(mf) # window: [1]
1

julia> grow!(mf, 2); median(mf) # window: [1,2]
1.5

julia> roll!(mf, 3); median(mf) # window: [2,3]
2.5

julia> shrink!(mf); median(mf) # window: [3]
3
```
