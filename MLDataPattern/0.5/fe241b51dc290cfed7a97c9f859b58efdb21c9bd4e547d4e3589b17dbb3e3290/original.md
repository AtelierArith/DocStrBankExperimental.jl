```
slidingwindow(data, size, [stride], [obsdim]) -> UnlabeledSlidingWindow
```

Return a vector-like view of the `data` for which each element is a fixed size "window" of `size` adjacent observations. By default these windows are not overlapping. Note that only complete windows are included in the output, which implies that it is possible for excess observations to be omitted from the view.

```julia-repl
julia> A = slidingwindow(1:20, 6)
3-element slidingwindow(::UnitRange{Int64}, 6) with element type SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 [1, 2, 3, 4, 5, 6]
 [7, 8, 9, 10, 11, 12]
 [13, 14, 15, 16, 17, 18]
```

Note that the values of `data` itself are not copied. Instead the function [`datasubset`](@ref) is called when `getindex` is invoked. To actually get a copy of the data at some window use the function [`getobs`](@ref).

```julia-repl
julia> A[1]
6-element SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 1
 ⋮
 6

julia> getobs(A, 1)
6-element Array{Int64,1}:
 1
 ⋮
 6
```

The optional parameter `stride` can be used to specify the distance between the start elements of each adjacent window. By default the stride is equal to the window size.

```julia-repl
julia> slidingwindow(1:20, 6, stride = 3)
5-element slidingwindow(::UnitRange{Int64}, 6, stride = 3) with element type SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 [1, 2, 3, 4, 5, 6]
 [4, 5, 6, 7, 8, 9]
 [7, 8, 9, 10, 11, 12]
 [10, 11, 12, 13, 14, 15]
 [13, 14, 15, 16, 17, 18]
```

The optional (keyword) parameter `obsdim` allows one to specify which dimension denotes the observations. see `LearnBase.ObsDim` for more detail.
