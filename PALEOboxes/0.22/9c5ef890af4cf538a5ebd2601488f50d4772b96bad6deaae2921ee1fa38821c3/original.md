```
setvalue!(par::Parameter, value)
```

Set Parameter to `value`.

Optionally (if [`Parameter`](@ref) has Type parameter `ParseFromString != Nothing`) parse `value` from a String.
