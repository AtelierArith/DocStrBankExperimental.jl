```
Buffer(device::T, samples_count, cyclic::Bool = false) where {T <: AbstractDeviceOrTrigger}
```

Initializes a new Buffer instance.

# Parameters

  * `device::AbstractDeviceOrTrigger` :  A device instance (either [`Device`](@ref) or [`Trigger`](@ref) to which the buffer belongs
  * `samples_count` : The size of the buffer in samples
  * `cyclic` : If set to true, the buffer is circular
