```
CoroutineBehavior(action)
```

Create a behavior which allows for explicit interruptions.

The given function `action(a::Agent, b::Behavior)` is called exactly once at the earliest available opportunity. The behavior may explicitly interrupt itself by calling `delay(b, millis)`, which immediately blocks the behavior for `millis` milliseconds.

# Examples:

```julia
@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, CoroutineBehavior() do a, b
    for ith = ("first", "second", "third")
      println("Pausing for the $ith time")
      delay(b, 500)
    end
  end)
end
```
