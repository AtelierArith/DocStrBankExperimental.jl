```
concrete_term(t::Term, data[, hint])
```

プレースホルダー `t` からデータソースとオプションのヒントに基づいて具体的な項を作成します。 `data` がテーブルの場合、適切な列を抽出するために `getproperty` が使用されます。

`hint` はヒントの `Dict{Symbol}` であるか、特定のヒント、具体的な項のタイプ（`ContinuousTerm` または `CategoricalTerm`）、または何らかの `<:AbstractContrasts` のインスタンスである場合、そのコントラストを使用して `CategoricalTerm` が作成されます。

ヒントが提供されない場合（または `hint==nothing`）、データの `eltype` が使用されます： `Number` は連続的であると見なされ、その他はすべてカテゴリカルであると見なされます。

# 例

```jldoctest
julia> concrete_term(term(:a), [1, 2, 3])
a(continuous)

julia> concrete_term(term(:a), [1, 2, 3], nothing)
a(continuous)

julia> concrete_term(term(:a), [1, 2, 3], CategoricalTerm)
a(DummyCoding:3→2)

julia> concrete_term(term(:a), [1, 2, 3], EffectsCoding())
a(EffectsCoding:3→2)

julia> concrete_term(term(:a), [1, 2, 3], Dict(:a=>EffectsCoding()))
a(EffectsCoding:3→2)

julia> concrete_term(term(:a), (a = [1, 2, 3], b = [0.0, 0.5, 1.0]))
a(continuous)
```
