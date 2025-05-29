```
CyclicBehavior(action)
```

Create a cyclic behavior that runs repeatedly at the earliest available opportunity. The `action(a::Agent, b::Behavior)` function is called when the behavior runs. The `onstart` and `onend` fields in the behavior may be set to functions that are called when the behavior is initialized and terminates. Both functions are called with similar parameters as `action`.

The running of cyclic behaviors may be controlled using `block(b)`, `restart(b)` and `stop(b)`.

# Examples:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, CyclicBehavior() do a, b
    @info "CyclicBehavior running..."
  end)
end
```
