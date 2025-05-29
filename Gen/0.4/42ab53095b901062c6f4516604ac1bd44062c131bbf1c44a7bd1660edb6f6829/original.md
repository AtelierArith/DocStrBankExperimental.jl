```
set_param_grad!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, grad_value)
```

Set the gradient accumlator for a trainable parameter of the generative function.
