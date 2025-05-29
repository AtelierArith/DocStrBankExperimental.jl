```
@method_def_constant [ValType=Val] [map_expr] method_call get_constant_method
```

Given a `method_call` expression of the form `f(::Type{T1}, ::Type{T2}, ..., ::Type{Ti}, ::ValType{::S}, ::Type{Ti+1}, ..., ::Type{Tn})`, generates a method definition for `get_constant_method` which returns an iterable with element type `S` of all of the compile-time constants contained in the `ValType` parameter of each definition of `f`. 

`get_constant_method` is a generated function and thus incurs no runtime overhead, but also contains backedges to each method instance of `f`, and so the output is recompiled when a new method definition of `f` is added. 

`ValType` must be a singleton type with a single parameter. Define `MacroUtilities.inner_param` to extract the innermost type parameter for your own custom types. 

If `map_expr` is provided, it must resolve to a function mapping the collection of constants of type `Vector{S}` to a `Expr`. Defaults to `MacroUtilities.default_extract_const_expr`. (Requires at least Julia 1.7)
