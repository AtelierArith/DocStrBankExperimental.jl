```
DebugWhenActive <: DebugAction
```

evaluate and print debug only if the active boolean is set. This can be set from outside and is for example triggered by [`DebugEvery`](@ref) on debugs on the subsolver.

This method does not perform any print itself but relies on it's children's prints.

For now, the main interaction is with [`DebugEvery`](@ref) which might activate or deactivate this debug

# Fields

  * `active`:        a boolean that can (de-)activated from outside to turn on/off debug
  * `always_update`: whether or not to call the order debugs with iteration `<=0` inactive state

# Constructor

```
DebugWhenActive(d::DebugAction, active=true, always_update=true)
```
