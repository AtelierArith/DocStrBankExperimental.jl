```
@var2string(var, strvar="")
```

Return string representation of `var`.

If `var` is a String variable, return the value of the variable.   Otherwise, return the string representation of `var` (or `strvar` if provided).

# Examples

```julia
julia> @var2string(CCSD)
"CCSD"
julia> CCSD = "UCCSD";
julia> @var2string(CCSD)
"UCCSD"
```
