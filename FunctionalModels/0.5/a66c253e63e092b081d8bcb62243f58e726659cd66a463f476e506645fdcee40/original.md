```julia
Parameter(value = 0.0; name) 
```

`Parameter` is a helper to create a parameter with default values. The default value determines the type and shape of the result. It also adds metadata to variables so that variable names don't clash. The viewable variable name is based on a `gensym`. `name` is stored as metadata, and when equations are flattened with `system`, variables are renamed to include subsystem names and the variable base name. 

For example, `Parameter(name = :R)` may show as `var"##R#1057"`, but after flattening, it will show as something like `ss₊r1₊R`  (`ss` and `r1` are subsystems).
