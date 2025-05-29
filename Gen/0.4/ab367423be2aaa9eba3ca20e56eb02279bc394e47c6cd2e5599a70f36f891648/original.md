```
set_param!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, value)
```

Set the value of a trainable parameter of the generative function.

NOTE: Does not update the gradient accumulator value.
