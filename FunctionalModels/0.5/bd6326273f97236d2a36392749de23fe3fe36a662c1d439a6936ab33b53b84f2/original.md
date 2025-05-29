```julia
Unknown(value = NaN; name = :u) 
```

`Unknown` is a helper to create a variable with a default value. The default value determines the type and shape of the result. It also adds metadata to variables so that variable names don't clash. The viewable variable name is based on a `gensym`. `name` is stored as metadata, and when equations are flattened with `system`, variables are renamed to include subsystem names and variable base name. 

For example, `Unknown(name = :v)` may show as `var"##v#1057"(t)`, but after flattening, it will show as something like `ss₊c1₊v(t)`  (`ss` and `c1` are subsystems).
