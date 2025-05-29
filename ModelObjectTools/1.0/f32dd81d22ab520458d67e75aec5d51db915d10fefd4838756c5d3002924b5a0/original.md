```
@modef typedef
```

This is slight modification of the @kwdef helper macro defined in Base. It ensures that the struct to which it applies can be effectively used   with the functions defined in this package. Specifically: (1) Every field must have a default value, or the macro throws an error; (2) It automatically creates a constructor with optional keyword     arguments in the same style as Base.@kwdef, but in addition, that     constructor checks whether all parameters are valid as defined by      the registering of variable names via addVarInfo().

# Examples

```julia-repl
julia> @modef struct ModelParams
                  myScalarParam::Float64 = 4.0
                  myVecParam::Vector{Float64} = [1.0, 2.0]
              end
ModelParams

julia> addVarInfo(:myScalarParam; lb = 0.0); addVarInfo(:myVecParam; normalization = :ordered);

julia> ModelParams()
ModelParams(4.0, [1.0, 2.0])

julia> ModelParams(myVecParam = [2.0, 1.0])
ERROR: [2.0, 1.0] is not a valid input for myVecParam.
Stacktrace:
[...]
```
