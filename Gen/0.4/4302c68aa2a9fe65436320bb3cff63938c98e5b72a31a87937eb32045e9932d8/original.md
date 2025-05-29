```
zero_param_grad!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol)
```

Reset the gradient accumlator for a trainable parameter of the generative function to all zeros.
