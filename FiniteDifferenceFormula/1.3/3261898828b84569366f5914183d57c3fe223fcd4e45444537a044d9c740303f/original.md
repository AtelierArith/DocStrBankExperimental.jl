`formulas`(orders = 1:3, min*num*of*points = 2, max*num*of*points = 5)

By default, the function prints all forward, backward, and central finite difference formulas for the 1st, 2nd, and 3rd derivatives, using 2 to 5 points.

# Examples

```julia-repl
# The following examples show all forward, backward, and central finite
# difference formulas for the specified derivatives, using 4 to 11 points.
julia> import FiniteDifferenceFormula as fd
julia> fd.formulas(2:5, 4, 11)       # the 2nd, 3rd, .., 5th derivatives
juliq> fd.formulas([2, 4, 7], 4, 11) # the 2nd, 4th, and 7th derivatives
julia> fd.formulas(3, 4, 11)         # the 3rd derivative
```
