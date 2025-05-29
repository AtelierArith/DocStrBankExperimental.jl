Mark the field as shared across roles. 

This only works on structs with empty default constructor. Internally the marked field will be initialized with a model created by [`get_model`](@ref). The model will be set when the Role is added to an agent.

# Example

```julia
@kwdef struct Model
    field::Int = 0
end
@role struct MyRole
    @shared
    my_model::Model # per agent the exact same in every agent.
end
```
