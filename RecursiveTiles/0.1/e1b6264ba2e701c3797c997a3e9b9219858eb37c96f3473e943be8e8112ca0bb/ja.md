```
ExtendScheme(s, [h=nothing])
```

スキーム `s` を拡張するためのファンクタで、変換 `h` を追加することによって、呼び出される各要素に対してインデックスを構築します。以下に示すように直接呼び出すこともできますが、最も一般的には `tile` または `tiles` に渡されます。

参照: [`Scheme`](@ref), [`@scheme`](@ref)

# 例

```jldoctest
julia> s = Scheme(sum, last);

julia> e = ExtendScheme(s, abs2 ∘ last);

julia> e([1, 2, 3])
((6, 3), 9)

julia> ExtendScheme(s)([1, 2, 3]) == s([1, 2, 3])
true

julia> e2 = ExtendScheme(e, first);

julia> e2([1, 2, 3])
(((6, 3), 9), 1)

julia> ExtendScheme(e)([1, 2, 3]) == e([1, 2, 3])
true
```
