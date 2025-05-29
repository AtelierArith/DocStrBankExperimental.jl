```
struct Parameters <: AbstractDict{Symbol, Any} ⋯ end
```

Container for model parameters. It functions as a `Dict` where the keys are the parameter names. Simple parameter values are stored directly. Special parameters depend on other parameters are are wrapped in the appropriate data structures to keep track of such dependencies. There are two types of special parameters - aliases and links.

Individual parameters can be accessed in two different ways - dot and bracket notation.

Read access by dot notation calls [`peval`](@ref) while bracket notation doesn't. This makes no difference for simple parameters. For special parameters, access by bracket notation returns its internal structure, while access by dot notation returns its current value depending on other parameters.

Write access is the same in both dot and bracket notation. The new parameter value is assigned directly in the case of simple parameter. To create an alias parameter, use the [`@alias`](@ref) macro. To create a link parameter use the [`@link`](@ref) macro.

See also: [`ModelParam`](@ref), [`peval`](@ref), [`@alias`](@ref), [`@link`](@ref), [`update_links!`](@ref).
