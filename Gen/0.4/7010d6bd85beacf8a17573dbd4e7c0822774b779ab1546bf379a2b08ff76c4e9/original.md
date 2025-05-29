```
value = get_param_grad(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol)
```

Get the current value of the gradient accumulator for a trainable parameter of the generative function.
