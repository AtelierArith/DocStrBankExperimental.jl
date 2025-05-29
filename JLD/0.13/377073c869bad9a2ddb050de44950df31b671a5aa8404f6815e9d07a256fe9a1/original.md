```julia
@load "filename.jld"
@load "filename.jld" var1 [var2 var3 ...]
```

Load the variables `var1`, `var2`, et cetera, contained in the file `filename.jld` into the current global scope.

If no variable names are specified, all variables from the file will be loaded.

Returns a `Vector` of `Symbol`s corresponding to the names of the loaded variables.
