```
init_param!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, value)
```

Initialize the the value of a named trainable parameter of a generative function.

Also generates the gradient accumulator for that parameter to `zero(value)`.

Example:

```julia
init_param!(foo, :theta, 0.6)
```
