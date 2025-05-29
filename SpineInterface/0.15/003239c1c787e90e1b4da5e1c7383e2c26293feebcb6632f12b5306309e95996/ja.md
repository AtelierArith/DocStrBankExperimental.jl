```
(<oc>::ObjectClass)(;<keyword arguments>)
```

`oc`クラスのオブジェクトに対応する[`Object`](@ref)インスタンスの`Array`。

# 引数

データベース内の`oc`に関連する各パラメータには、それにちなんだ名前のキーワード引数があります。目的は、そのパラメータの特定の値で結果をフィルタリングすることです。

# 例

```jldoctest
julia> using SpineInterface;


julia> url = "sqlite:///" * joinpath(dirname(pathof(SpineInterface)), "..", "examples/data/example.sqlite");


julia> using_spinedb(url)


julia> sort(node())
5-element Vector{Union{Int64, Object, TimeSlice}}:
 Dublin
 Espoo
 Leuven
 Nimes
 Sthlm

julia> commodity(state_of_matter=:gas)
1-element Vector{Union{Int64, Object, TimeSlice}}:
 wind
```
