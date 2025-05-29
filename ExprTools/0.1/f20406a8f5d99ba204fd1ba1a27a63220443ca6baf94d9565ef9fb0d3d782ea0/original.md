```
args_tuple_expr(signature_def::Dict{Symbol})
args_tuple_expr(arg_exprs)
```

For `arg_exprs` being a list of positional argument expressions from a signature, of a form such as `[:(x::Int), :(y::Float64), :(z::Vararg)]`, or being a whole `signature_def` `Dict` containing a `signature_def[:args]` value of that form.

This returns a tuple expression containing all of the args by name. It correctly handles splatting for things that are `Vararg` typed, e.g for the prior example `:((x, y, z...))`

This is useful for modifying the `signature_def[:body]`. For example, one could printout all the arguments via

```julia
signature_def[:body] = quote
    args = $(args_tuple_expr(signature_def))
    println("args = ",args)
    $(signature_def[:body]) # insert old body
end
```

A more realistic use case is if you want to insert a call to another function that accepts the same arguments as the original function.
