```
BackoffBehavior(action, millis)
```

Create a behavior that runs after `millis` milliseconds. The `action(a::Agent, b::Behavior)` function is called when the behavior runs. The behavior may be scheduled to re-run in `t` milliseconds by calling `backoff(b, t)`.

The `onstart` and `onend` fields in the behavior may be set to functions that are called when the behavior is initialized and terminates. Both functions are called with similar parameters as `action`.

The `BackoffBehavior` constructor is simply syntactic sugar for a `WakerBehavior` that is intended to be rescheduled often using `backoff()`.

# Examples:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  # a behavior that will run for the first time in 5 seconds, and subsequently
  # every 2 seconds
  add(a, BackoffBehavior(5000) do a, b
    @info "Backoff!"
    backoff(b, 2000)
  end)
end
```
