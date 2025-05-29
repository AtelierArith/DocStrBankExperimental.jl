```
@load filename var1 [var2 ...]
```

Load one or more variables `var1,...` from JLD2 file `filename` into the current scope and return a vector of the loaded variable names.

For interactive use, the form `@load "somefile.jld2"` will load all variables from `"somefile.jld2"` into the current scope. This form only supports literal file names and should be avoided in more permanent code so that it's clear where the variables come from.

# Example

To load the variables `hello` and `foo` from the file example.jld2, use

```julia
@load "example.jld2" hello foo
```
