```
@save filename var1 [var2 ...]
@save filename {compress=true} var1 name2=var2
```

Write one or more variables `var1,...` from the current scope to a JLD2 file `filename`.

For interactive use you can save all variables in the current module's global scope using `@save filename`. More permanent code should prefer the explicit form to avoid saving unwanted variables.

# Example

To save the string `hello` and array `xs` to the JLD2 file example.jld2:

```julia
hello = "world"
xs = [1,2,3]
@save "example.jld2" hello xs
```

For passing options to the saving command use `{}`

```julia
@save "example.jld2" {compress=true} hello xs
```

For saving variables under a different name use regular assignment syntax

```julia
@save "example.jld2" greeting=hello xarray = xs
```
