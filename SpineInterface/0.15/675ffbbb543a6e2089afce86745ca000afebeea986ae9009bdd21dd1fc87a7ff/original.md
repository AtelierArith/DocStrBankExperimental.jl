```
(<p>::Parameter)(;<keyword arguments>)
```

The value of parameter `p` for a given arguments.

# Arguments

  * For each object class associated with `p` there is a keyword argument named after it. The purpose is to retrieve the value of `p` for a specific object.
  * For each relationship class associated with `p`, there is a keyword argument named after each of the object classes involved in it. The purpose is to retrieve the value of `p` for a specific relationship.
  * `i::Int64`: a specific index to retrieve in case of an array value (ignored otherwise).
  * `t::TimeSlice`: a specific time-index to retrieve in case of a time-varying value (ignored otherwise).
  * `inds`: indexes for navigating a `Map` (ignored otherwise). Tuples correspond to navigating nested `Maps`.
  * `_strict::Bool`: whether to raise an error or return `nothing` if the parameter is not specified for the given arguments.

# Examples

```jldoctest
julia> using SpineInterface;


julia> url = "sqlite:///" * joinpath(dirname(pathof(SpineInterface)), "..", "examples/data/example.sqlite");


julia> using_spinedb(url)


julia> tax_net_flow(node=node(:Sthlm), commodity=commodity(:water))
4

julia> demand(node=node(:Sthlm))
3-element Vector{Float64}:
 21.0
 17.0
  9.0

julia> demand(node=node(:Sthlm), i=2)
17.0
```
