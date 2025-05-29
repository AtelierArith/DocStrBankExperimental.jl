```
prim2cons(q, equations)
```

Convert the primitive variables `q` to the conserved variables for a given set of `equations`. `q` is a vector type of the correct length `nvariables(equations)`. Notice the function doesn't include any error checks for the purpose of efficiency, so please make sure your input is correct. The inverse conversion is performed by [`cons2prim`](@ref).
