```
GlobalMeanPool()
```

Global mean pooling layer.

Transforms (w,h,c,b)-shaped input into (1,1,c,b)-shaped output, by performing mean pooling on the complete (w,h)-shaped feature maps.

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);

julia> m = Chain(Conv((3,3), 3 => 7), GlobalMeanPool());

julia> m(xs) |> size
(1, 1, 7, 50)
```
