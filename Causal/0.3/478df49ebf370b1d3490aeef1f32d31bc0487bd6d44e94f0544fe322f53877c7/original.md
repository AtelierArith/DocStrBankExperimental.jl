```julia
mutable struct TaskManager{T, S, IP, OP, CB}
```

Constructs a `TaskManager` with `pairs`. `pairs` is a dictionary whose keys are components and values are component tasks. Component tasks are constructed correponding to the components. A `TaskManager` is used to keep track of the component task launched corresponding to components.

# Fields

  * `pairs::Dict`: Node-task pair
  * `handshakeport::Any`: Handshake port of task manager. Used for handshake
  * `triggerport::Any`: Trigger port of task manager. Used to trigger components
  * `callbacks::Any`: Callback set. [`Callback`](@ref)
  * `name::Symbol`: Name of task manager
  * `id::Base.UUID`: Unique identifier

```
