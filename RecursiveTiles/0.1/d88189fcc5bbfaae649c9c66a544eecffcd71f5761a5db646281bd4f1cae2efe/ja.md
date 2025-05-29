```
Scheme(f, [g=nothing])
```

タイルの各要素を構築するために適用される変換である `f` と、タイルのインデックスを構築するために適用される変換である `g` から構成されるファンクタです。以下に示すように直接呼び出すこともできますが、最も一般的には `tile` または `tiles` に渡されます（おそらく1つ以上の `ExtendScheme` でラップされた後に）。

参照: [`ExtendScheme`](@ref), [`@scheme`](@ref)

# 例

```jldoctest
julia> s = Scheme(sum, last);

julia> s([1, 2, 3])
(6, 3)

julia> Scheme(sum)([1, 2, 3])
6
```
