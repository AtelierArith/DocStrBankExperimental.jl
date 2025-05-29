```
get_device(x) -> dev::AbstractDevice | Exception | Nothing
```

If all arrays (on the leaves of the structure) are on the same device, we return that device. Otherwise, we throw an error. If the object is device agnostic, we return `nothing`.

!!! note
    Trigger Packages must be loaded for this to return the correct device.


## Special Retuened Values

  * `nothing` – denotes that the object is device agnostic. For example, scalar, abstract range, etc.
  * `UnknownDevice()` – denotes that the device type is unknown.

See also [`get_device_type`](@ref) for a faster alternative that can be used for dispatch based on device type.
