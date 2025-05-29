```
onecold(y::AbstractArray, labels = 1:size(y,1))
```

Roughly the inverse operation of [`onehot`](@ref) or [`onehotbatch`](@ref):  This finds the index of the largest element of `y`, or each column of `y`,  and looks them up in `labels`.

If `labels` are not specified, the default is integers `1:size(y,1)` – the same operation as `argmax(y, dims=1)` but sometimes a different return type.

# Examples

```jldoctest
julia> onecold([false, true, false])
2

julia> onecold([0.3, 0.2, 0.5], (:a, :b, :c))
:c

julia> onecold([ 1  0  0  1  0  1  0  1  0  0  1
                 0  1  0  0  0  0  0  0  1  0  0
                 0  0  0  0  1  0  0  0  0  0  0
                 0  0  0  0  0  0  1  0  0  0  0
                 0  0  1  0  0  0  0  0  0  1  0 ], 'a':'e') |> String
"abeacadabea"
```
