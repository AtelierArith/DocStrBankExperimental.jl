```
add_parameters(model::InfiniteModel,
               params::DependentParameters,
               names::Vector{String}
               )::Vector{GeneralVariableRef}
```

Add `params` to `model` and return an appropriate container of the dependent infinite parameter references. This is intended as an internal method for use with [`@infinite_parameter`](@ref). However, if desired users can use this to add a `DependentParameters` object to `model`. Here, `names` denote the name  of each parameter. 

**Example**

```julia-repl
julia> using Distributions

julia> dist = MvNormal(ones(3)); # 3 dimensional

julia> domain = MultiDistributionDomain(dist); # 3 dimensional

julia> params = DependentParameters(domain, Dict{Vector{Float64}, Set{DatatType}}(), 10);

julia> prefs = add_parameters(model, params, ["par1", "par2", "par3"])
3-element Array{GeneralVariableRef,1}:
 par1
 par2
 par3
```
