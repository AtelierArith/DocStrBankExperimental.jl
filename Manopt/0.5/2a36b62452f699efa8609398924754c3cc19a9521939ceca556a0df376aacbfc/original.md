```
RecordWhenActive <: RecordAction
```

record action that only records if the `active` boolean is set to true. This can be set from outside and is for example triggered by |`RecordEvery`](@ref) on recordings of the subsolver. While this is for sub solvers maybe not completely necessary, recording values that are never accessible, is not that useful.

# Fields

  * `active`:        a boolean that can (de-)activated from outside to turn on/off debug
  * `always_update`: whether or not to call the inner debugs with nonpositive iterates (init/reset)

# Constructor

```
RecordWhenActive(r::RecordAction, active=true, always_update=true)
```
