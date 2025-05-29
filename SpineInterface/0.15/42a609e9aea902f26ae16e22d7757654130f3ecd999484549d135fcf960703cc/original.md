```
(<rc>::RelationshipClass)(;<keyword arguments>)
```

An `Array` of [`Object`](@ref) tuples corresponding to the relationships of class `rc`.

# Arguments

  * For each object class in `rc` there is a keyword argument named after it. The purpose is to filter the result by an object or list of objects of that class, or to accept all objects of that class by specifying `anything` for this argument.
  * `_compact::Bool=true`: whether or not filtered object classes should be removed from the resulting tuples.
  * `_default=[]`: the default value to return in case no relationship passes the filter.

# Examples

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
# `sort()` doesn't work with Base.Generator, use `collect()` instead.

julia> node__commodity(commodity=commodity(:gas), _default=:nogas)
:nogas
```
