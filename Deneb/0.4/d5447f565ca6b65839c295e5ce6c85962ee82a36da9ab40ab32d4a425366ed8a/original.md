```
interactive_scales(;bindx=true, bindy=true, shift_on_y=false)
```

Creates a `ParamsSpec` that can be composed to other specs to create interactive pan (mouse hold and drag) and zoom (mouse wheel) charts. `bindx` and `bindy` specify if the `x` and `y` channels are to be bound. If `shift_on_y` is true, then the shift key must be hold to pan and zoom in the `y` channel.
