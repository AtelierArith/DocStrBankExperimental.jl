```
indices(p::Parameter, [c::Union{ObjectClass,RelationshipClass}]; kwargs...)
```

`p`の値が`nothing`でないすべてのオブジェクトとリレーションシップに対するイテレータ。

# 引数

  * `p`が定義されている各オブジェクトクラスに対して、それにちなんだ名前のキーワード引数があります。同様に、`p`が定義されている各リレーションシップクラスに対して、その中の各オブジェクトクラスにちなんだ名前のキーワード引数があります。これらの引数の目的は、特定のクラスのオブジェクトまたはオブジェクトのリストによって結果をフィルタリングすること、または対応する引数に`anything`を指定することでそのクラスのすべてのオブジェクトを受け入れることです。

# 例

```jldoctest
julia> using SpineInterface;


julia> url = "sqlite:///" * joinpath(dirname(pathof(SpineInterface)), "..", "examples/data/example.sqlite");


julia> using_spinedb(url)


julia> collect(indices(tax_net_flow))
1-element Vector{@NamedTuple{node::Object, commodity::Object}}:
 (node = Sthlm, commodity = water)

julia> collect(indices(demand))
5-element Vector{Object}:
 Dublin
 Espoo
 Leuven
 Nimes
 Sthlm
```
