```
set_inactive(sc::SpeedController, inactive::Bool)
```

De-activate the speed controller if the parameter inactive is true, otherwise activate it and reset the integrator and the limiter.

## Parameters

  * sc::[SpeedController](@ref): the speed controller to de-activate or activate

## Returns

  * nothing
