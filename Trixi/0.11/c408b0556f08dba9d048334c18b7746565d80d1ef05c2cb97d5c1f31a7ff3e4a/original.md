```
cons2entropy(u, equations)
```

Convert the conserved variables `u` to the entropy variables for a given set of `equations` with chosen standard [`entropy`](@ref).

`u` is a vector type of the correct length `nvariables(equations)`. Notice the function doesn't include any error checks for the purpose of efficiency, so please make sure your input is correct. The inverse conversion is performed by [`entropy2cons`](@ref).
