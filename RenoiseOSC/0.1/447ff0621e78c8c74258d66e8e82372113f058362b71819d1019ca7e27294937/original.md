```
setparam(key::Union{AbstractString,Integer}, value::Real; track::Integer=-1, device::Integer=-1)
```

Set the parameter of any device by its name or index. `value` is clamped between `0.0` and `1.0`. When unspecified, track and device default to the currently selected track and device.
