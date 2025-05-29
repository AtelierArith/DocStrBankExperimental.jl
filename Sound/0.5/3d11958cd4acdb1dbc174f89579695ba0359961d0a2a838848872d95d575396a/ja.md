```
sound(output_device_index::Int, x, S::Real = framerate(x); kwargs...)
```

`x`の音を`devices()[output_device_index]`を使用して再生します。
