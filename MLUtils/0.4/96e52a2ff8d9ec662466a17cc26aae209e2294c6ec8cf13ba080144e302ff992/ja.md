```
flatten(x::AbstractArray)
```

任意の形状の入力を行列形状の出力に変換し、最後の次元のサイズを保持します。

関連項目として[`unsqueeze`](@ref)があります。

# 例

```jldoctest
julia> rand(3,4,5) |> flatten |> size
(12, 5)
```
