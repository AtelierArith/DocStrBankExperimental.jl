```
indices(p::Parameter, [c::Union{ObjectClass,RelationshipClass}]; kwargs...)
```

An iterator over all objects and relationships where the value of `p` is different than `nothing`.

# Arguments

  * For each object class where `p` is defined, there is a keyword argument named after it; similarly, for each relationship class where `p` is defined, there is a keyword argument named after each object class in it. The purpose of these arguments is to filter the result by an object or list of objects of an specific class, or to accept all objects of that class by specifying `anything` for the corresponding argument.

# Examples

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
