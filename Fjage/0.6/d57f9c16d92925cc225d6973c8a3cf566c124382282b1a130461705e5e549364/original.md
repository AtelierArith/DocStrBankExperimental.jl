```
TickerBehavior(action, millis)
```

Create a behavior that runs periodically every `millis` milliseconds. The `action(a::Agent, b::Behavior)` function is called when the behavior runs. The `onstart` and `onend` fields in the behavior may be set to functions that are called when the behavior is initialized and terminates. Both functions are called with similar parameters as `action`.

# Examples:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, TickerBehavior(5000) do a, b
    @info "Tick!"
  end)
end
```
