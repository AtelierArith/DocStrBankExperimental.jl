```
@linear_broadcastable T
```

Add the type `T` to the types that participate in broadcasting for linear combinations. By default, only the types `AbstractLinear` and `Number` are available. (A few others happen to work as well, for example `AbstractChar`.)

See also [`LinearCombinations.LinearStyle`](@ref).
