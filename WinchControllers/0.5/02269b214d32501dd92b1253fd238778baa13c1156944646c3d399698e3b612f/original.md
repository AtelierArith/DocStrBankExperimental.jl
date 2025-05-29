```
on_timer(w::Winch)
```

Update the winch. Must be called once per time-step. calculates and updates the winch acceleration `w.acc` using a loop.

## Parameters

  * w::Winch: Reference to the [Winch](@ref) component

## Returns

  * nothing
