```
ConcurrentQueue{T}()
```

型 `T` のオブジェクトの同時キュー。

`push!` を使用して尾に要素を挿入し、[`maybepopfirst!`](@ref) を使用して先頭の要素を取得して削除します。

実装の詳細: マイケルとスコットのキューを実装しています。

# 例

```jldoctest ConcurrentQueue
julia> using ConcurrentCollections

julia> queue = ConcurrentQueue{Int}();

julia> push!(queue, 1);

julia> push!(queue, 2);

julia> popfirst!(queue)
1

julia> maybepopfirst!(queue)
Some(2)

julia> maybepopfirst!(queue)  # 何も返さない
```
