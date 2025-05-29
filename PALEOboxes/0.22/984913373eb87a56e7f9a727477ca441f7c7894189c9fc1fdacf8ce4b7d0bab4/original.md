```
setvalueanddefault!(par::Parameter, value; freeze=false)
```

Set Parameter value and default to `value`.

Optionally (if [`Parameter`](@ref) has Type parameter `ParseFromString != Nothing`) parse `value` from a String.
