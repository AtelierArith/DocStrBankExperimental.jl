```
mutable struct Winch
```

Component, that calculates the acceleration of the tether based on the tether force and the set speed (= synchronous speed). Asynchronous motor model and drum inertia are taken into account. Used for testing of the winch controller.

## Fields

  * `wcs::WinchControllers.WCSettings`
  * `set::KiteUtils.Settings`
  * `wm::WinchModels.AsyncMachine`: Default: AsyncMachine(set)
  * `v_set::Float64`: Default: 0
  * `force::Float64`: Default: 0
  * `acc::Float64`: Default: 0
  * `speed::Float64`: Default: 0
