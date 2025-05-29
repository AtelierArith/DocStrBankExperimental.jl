```julia
mutable struct Callback{CN, AC}
```

Constructs a `Callback` from `condition` and `action`. The `condition` and `action` must be a single-argument function. The `condition` returns `true` if the condition it checks occurs, otherwise, it returns `false`. `action` performs the specific action for which the `Callback` is constructed. A `Callback` can be called by passing its single argument which is mostly bound to the `Callback`.

# Fields

  * `condition::Any`: Condition function of callback. Expected to be a single-argument function
  * `action::Any`: Action of the callback. Expected to be a single-argument fucntion
  * `enabled::Bool`: If true, callback is activated
  * `id::Base.UUID`: Unique identifier

# Example

```julia
julia> struct Object  # Define a dummy type.
       x::Int 
       clb::Callback 
       end

julia> cond(obj) = obj.x > 0;  # Define callback condition.

julia> action(obj) = println("obj.x = ", obj.x); # Define callback action.

julia> obj = Object(1, Callback(condition=cond, action=action))
Object(1, Callback(condition:cond, action:action))

julia> obj.clb(obj)  # Call the callback bound `obj`.
obj.x = 1
```
