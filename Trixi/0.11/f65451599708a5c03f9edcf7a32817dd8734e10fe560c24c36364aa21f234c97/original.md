```
entropy2cons(w, equations)
```

Convert the entropy variables `w` based on a standard [`entropy`](@ref) to the conserved variables for a given set of `equations`. `u` is a vector type of the correct length `nvariables(equations)`. Notice the function doesn't include any error checks for the purpose of efficiency, so please make sure your input is correct. The inverse conversion is performed by [`cons2entropy`](@ref).
