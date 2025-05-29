```
@findall ids :symbol
@findall ids r"Regular Expression"
@findall [ids1, ids2] [:sybmol1, :symbol2]
@findall [ids1, ids2] r"Regular Expression"
```

Searches for specified fields within single/multiple IDS objects, while capturing their names into IDS*Field*Finder.root_name

See also [`findall(root_ids::Union{IDS,IDSvector}, target::Union{Symbol,AbstractArray{Symbol},Regex}=r""; kwargs)`](@ref) which this macro calls after expansion.

# Arguments

  * `root_ids:: Root IDS objects to search.
  * `target_fields::Union{Symbol, AbstractArray{Symbol}, Regex}: Fields to search for, specified by a single symbol, array of symbols, or regular expression.

# Returns

  * `Vector{IDS_Field_Finder}`: A vector of `IDS_Field_Finder` structures, each containing details on a located field such as parent IDS, root IDS, field type, and full field path.

# Example

```julia-repl
julia> @findall [dd1, dd2] [:psi, :j_tor]
julia> @findall [dd1, dd2] r"psi"

julia> eqt = dd.equilibrium.time_slice[]

julia> @findall eqt :psi
julia> @findall eqt r"global.*psi"
```
