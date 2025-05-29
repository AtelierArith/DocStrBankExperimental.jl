````
mlmformula(ex)

Capture and parse a formula expression for matrix linear model.

The `@mlmformula` domain-specific language serves the purpose of facilitating table-to-matrix transformations.
It is structured to be intuitive for users who have experience with other statistical software.
An elementary formula in this language consists of individual terms. These terms may either be symbols that reference
data columns or literal numbers `0` or `1`. They are combined by the operators `+`, `&`, and `*`. 
To ensure correct parsing of the formula, the `@mlmformula`` macro needs to be invoked within parentheses. 
This macro is built upon the `@formula` macro from the `StatsModels.jl` package.

# Example
```julia
julia> @mlmformula(1 + varA * VarB)
1
varA(unknown)
VarB(unknown)
varA(unknown) & VarB(unknown)
```
````
