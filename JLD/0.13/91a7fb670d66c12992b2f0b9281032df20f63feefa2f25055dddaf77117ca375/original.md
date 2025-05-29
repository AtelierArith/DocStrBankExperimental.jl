```julia
@save "filename.jld" var1 [var2 var3 ...]
@save compress=true "filename.jld" var1 [var2 var3 ...]
```

Save the variables `var1` (and optionally `var2`, `var3`, etc.) to a JLD file "filename.jld". Optionally you may specify `compress=true` or `compress=false` as the first argument, to specify whether the resulting `.jld` file should be compressed (default=`false`).
