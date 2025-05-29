```
get_device_type(x) -> Type{<:AbstractDevice} | Exception | Type{Nothing}
```

Similar to [`get_device`](@ref) but returns the type of the device instead of the device itself. This value is often a compile time constant and is recommended to be used instead of [`get_device`](@ref) where ever defining dispatches based on the device type.

!!! note
    Trigger Packages must be loaded for this to return the correct device.


## Special Retuened Values

  * `Nothing` – denotes that the object is device agnostic. For example, scalar, abstract range, etc.
  * `UnknownDevice` – denotes that the device type is unknown.
