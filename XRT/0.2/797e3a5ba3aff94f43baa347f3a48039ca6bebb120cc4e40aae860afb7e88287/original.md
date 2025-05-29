```julia
get_xclbin_uuid(; device) -> XRT.XRTWrap.UUIDAllocated

```

Returns the UUID of the xclbin image that is currently loaded on the active device. The device can be changed by setting the `device` keyword parameter.
