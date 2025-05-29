```
onecold(y::AbstractArray, labels = 1:size(y,1))
```

おおよそ [`onehot`](@ref) または [`onehotbatch`](@ref) の逆操作です：これは `y` の最大要素のインデックス、または `y` の各列のインデックスを見つけ、`labels` でそれらを参照します。

`labels` が指定されていない場合、デフォルトは整数 `1:size(y,1)` です – これは `argmax(y, dims=1)` と同じ操作ですが、時には異なる戻り値の型になります。

# 例

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
