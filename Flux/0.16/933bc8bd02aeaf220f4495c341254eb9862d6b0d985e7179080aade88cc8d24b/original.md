```
GlobalMaxPool()
```

Global max pooling layer.

Transforms (w,h,c,b)-shaped input into (1,1,c,b)-shaped output, by performing max pooling on the complete (w,h)-shaped feature maps.

See also [`MaxPool`](@ref), [`GlobalMeanPool`](@ref).

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((3,3), 3 => 7), GlobalMaxPool());

julia> m(xs) |> size
(1, 1, 7, 50)

julia> GlobalMaxPool()(rand(3,5,7)) |> size  # preserves 2 dimensions
(1, 5, 7)
```
