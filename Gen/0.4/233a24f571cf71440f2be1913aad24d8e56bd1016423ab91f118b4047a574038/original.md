```
DynamicDSLFunction{T} <: GenerativeFunction{T,DynamicDSLTrace}
```

A generative function based on a shallowly embedding modeling language based on Julia functions.

Constructed using the `@gen` keyword. Most methods in the generative function interface involve a end-to-end execution of the function.
