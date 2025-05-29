```
(<rc>::RelationshipClass)(;<keyword arguments>)
```

クラス `rc` の関係に対応する [`Object`](@ref) タプルの `Array`。

# 引数

  * `rc` の各オブジェクトクラスには、それにちなんだ名前のキーワード引数があります。この目的は、そのクラスのオブジェクトまたはオブジェクトのリストで結果をフィルタリングすること、またはこの引数に `anything` を指定することでそのクラスのすべてのオブジェクトを受け入れることです。
  * `_compact::Bool=true`: フィルタリングされたオブジェクトクラスを結果のタプルから削除するかどうか。
  * `_default=[]`: フィルタを通過する関係がない場合に返すデフォルト値。

# 例

```jldoctest
julia> using SpineInterface;


julia> url = "sqlite:///" * joinpath(dirname(pathof(SpineInterface)), "..", "examples/data/example.sqlite");


julia> using_spinedb(url)


julia> sort(node__commodity())
5-element Vector{NamedTuple{K, V} where {K, V<:Tuple{Union{Int64, Object, TimeSlice}, Vararg{Union{Int64, Object, TimeSlice}}}}}:
 (node = Dublin, commodity = wind)
 (node = Espoo, commodity = wind)
 (node = Leuven, commodity = wind)
 (node = Nimes, commodity = water)
 (node = Sthlm, commodity = water)

julia> node__commodity(commodity=commodity(:water))
2-element Vector{Object}:
 Nimes
 Sthlm

julia> node__commodity(node=(node(:Dublin), node(:Espoo)))
1-element Vector{Object}:
 wind

julia> sort(node__commodity(node=anything))
2-element Vector{Object}:
 water
 wind

julia> collect(node__commodity(commodity=commodity(:water), _compact=false))
2-element Vector{@NamedTuple{node::Object, commodity::Object}}:
 (node = Nimes, commodity = water)
 (node = Sthlm, commodity = water)
# `sort()` は Base.Generator では機能しないため、代わりに `collect()` を使用してください。

julia> node__commodity(commodity=commodity(:gas), _default=:nogas)
:nogas
```
