```Julia
load_xclbin!(xclbin::XRT.Xclbin; device, force) -> XRT.UUID
load_xclbin!(path::String; device, force) -> XRT.UUID

```

Loads an [`XRT.Xclbin`](@ref) object on the current active device if it is not yet loaded onto it. The function returns the UUID of the xclbin. `XRT.program!` is an alias for `load_xclbin!`.

**Keywords**

**`device`** The target device can be changed by setting the `device` keyword parameter.

**`force`** Forces the Xclbin to be loaded onto the device.
