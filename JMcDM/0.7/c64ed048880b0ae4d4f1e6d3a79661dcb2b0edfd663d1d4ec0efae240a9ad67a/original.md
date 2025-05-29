```
    mcdm(df, w, fns, method)

Perform selected method for a given decision matrix, weight vector, and function list.
```

# Arguments:

  * `df::Matrix`: n × m matrix of decision matrix in type of Matrix.
  * `weights::Array{Float64, 1}`: m-vector of weights for criteria.
  * `fs::Array{Function, 1}`: m-vector of functions that are either maximize or minimize for each single criterion.
  * `method::MCDMMethod`: Preferred MCDMMethod.

# Description

The method is one of the subtypes of MCDMMethod type. See examples.

# Output

  * `::MCDMResult`: An object derived from subtypes of MCDMResult type.

# Examples

```julia-repl

julia> subtypes(MCDMMethod)
23-element Vector{Any}:
 ArasMethod
 CocosoMethod
 CodasMethod
 CoprasMethod
 CriticMethod
 EdasMethod
 ElectreMethod
 GreyMethod
 LMAWMethod
 LOPCOWMethod
 MabacMethod
 MaircaMethod
 MarcosMethod
 MERECMethod
 MooraMethod
 MoosraMethod
 OCRAMethod
 PIVMethod
 PrometheeMethod
 PSIMethod
 ROVMethod
 SawMethod
 TopsisMethod
 VikorMethod
 WaspasMethod
 WPMMethod


julia> # mcdm() for Topsis:
julia> # mcdm(df, w, fns, TopsisMethod())

julia> # mcdm() for Saw:
julia> # mcdm(df, w, fns, SawMethod())

julia> # mcdm() with optional parameters:
julia> # mcdm(df, w, fns, GreyMethod(0.6))
```
