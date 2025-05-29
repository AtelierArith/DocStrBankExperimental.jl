```
raw_status(model::GenericModel)
```

Return the reason why the solver stopped in its own words (that is, the MathOptInterface model attribute [`MOI.RawStatusString`](@ref)).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> raw_status(model)
"optimize not called"
```
