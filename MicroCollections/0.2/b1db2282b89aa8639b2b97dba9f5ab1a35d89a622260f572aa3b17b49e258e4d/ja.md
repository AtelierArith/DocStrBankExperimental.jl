```
OneHotArray(index => value, shape) -> array::AbstractArray
```

`isequal(array[index], value)`となる`array`を作成します。`index`以外のインデックスの値は未定義です。

現在、この配列タイプは、`BangBang.Extras.broadcast_inplace!!`の第二引数として、またはFLoops.jlの`@reduce`の入力引数としてのみ有用です。

# 例

```jldoctest
julia> using MicroCollections, BangBang.Extras

julia> broadcast_inplace!!(+, ones(Int64, 4), OneHotVector(2 => 3, 4))
4-element Vector{Int64}:
 1
 4
 1
 1

julia> using InitialValues

julia> broadcast_inplace!!(+, InitialValue(+), OneHotVector(2 => 3, 4))
4-element Vector{Int64}:
 0
 3
 0
 0
```
