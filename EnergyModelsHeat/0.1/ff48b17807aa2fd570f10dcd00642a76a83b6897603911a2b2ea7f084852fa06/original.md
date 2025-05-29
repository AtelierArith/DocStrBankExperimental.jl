```
ResourceHeat{IDT,TS<:TimeProfile,TR<:TimeProfile} <: Resource

ResourceHeat(id, t_supply::TimeProfile, t_return::TimeProfile)
ResourceHeat(id, t_supply::TimeProfile)
ResourceHeat(id, t_supply::Real, t_return::Real)
ResourceHeat(id, t_supply::Real)
```

A resource for heat.

# Fields

  * **`id::IDT`** is the name/identifyer of the resource.
  * **`t_supply::TS`** is the supply temperature in °C as a `TimeProfile`. Providing a single number will be translated to a `FixedProfile`.
  * **`t_return::TR`** is the return temperature in °C as a `TimeProfile`. Providing a single number will be translated to a `FixedProfile`. This field is optional, and will be set to zero if no value is provided.
