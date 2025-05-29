```
ConcurrentStack{T}()
```

型 `T` のオブジェクトの同時スタック。

要素を挿入するには `push!` を使用し、要素を取得して削除するには [`maybepop!`](@ref) を使用します。

これは Treiber スタックを実装しています。

# 例

```jldoctest ConcurrentStack
julia> using ConcurrentCollections

julia> stack = ConcurrentStack{Int}();

julia> push!(stack, 1);

julia> push!(stack, 2);

julia> pop!(stack)
2

julia> maybepop!(stack)
Some(1)

julia> maybepop!(stack)  # 何も返さない
```
