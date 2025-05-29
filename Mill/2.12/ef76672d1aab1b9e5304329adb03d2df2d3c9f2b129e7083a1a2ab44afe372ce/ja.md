```
LazyModel([Name::Symbol], m::AbstractMillModel)
LazyModel{Name}(m::AbstractMillModel)
```

新しい[`LazyModel`](@ref)を名前`Name`とモデル`m`で構築します。

モデルノードの代わりに任意の関数を`m`として渡すことも可能です。その場合、[`ArrayNode`](@ref)にラップされます。

# 例

```jldoctest
julia> LazyModel{:Sentence}(ArrayModel(Dense(2, 2)))
LazyModel{Sentence}
  ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> LazyModel(:Sentence, Dense(2, 2))
LazyModel{Sentence}
  ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
```

参照: [`AbstractMillModel`](@ref), [`LazyNode`](@ref), [`Mill.unpack2mill`](@ref).
