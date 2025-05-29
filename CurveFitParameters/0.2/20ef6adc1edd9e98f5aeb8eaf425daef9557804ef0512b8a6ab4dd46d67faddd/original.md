Type for a set of model parameters - wraps an `OrderedDict{String, Parameter}`. Implements the `AbstractDict` interface. Single `Parameter`'s can be accessed via `params.name` or `params["name"]`.

# Constructor:

```
Parameters()
```

Constructs an empty set of parameters.

```
Parameters(x::AbstractVector{<:Real}, names::AbstractVector{<:AbstractString}, lower_bounds=nothing, upper_bounds=nothing, vary=nothing)
```

Construct a set of parameters from `Vector`'s.
