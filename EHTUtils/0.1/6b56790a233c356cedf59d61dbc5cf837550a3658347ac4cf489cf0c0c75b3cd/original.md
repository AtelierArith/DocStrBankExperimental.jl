```
unitconv(unit1, unit2)
```

Derive the conversion factor from unit1 to unit2. The value in unit1 can be converted to that in unit2 by mutiplying this conversion factor.

# Examples

```julia-repl
julia> # Converting 1K to mK
julia> val2 = 1 * unitconv(u"K", u"mK") # value 2 will be 1000 
```
