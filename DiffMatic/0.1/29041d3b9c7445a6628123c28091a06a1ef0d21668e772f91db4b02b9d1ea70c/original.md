```
to_std(expr; format = StdStr())
```

Convert the expression `expr` to standard notation.

  * `format`: Output format. Can be one of:

      * [`StdStr`](@ref): String format.
      * [`JuliaFunc`](@ref): Julia function.

Examples:

```jldoctest to_std
@matrix A
@vector x

to_std(gradient(x' * A * x, x))

# output

"Aᵀx + Ax"
```

```julia
to_std(gradient(x' * A * x, x); format = JuliaFunc())

# output

quote
    #= ... =#
    function generated_function(A, x)
        #= ... =#
        #= ... =#
        return transpose(A) * x + A * x
    end
end
```
