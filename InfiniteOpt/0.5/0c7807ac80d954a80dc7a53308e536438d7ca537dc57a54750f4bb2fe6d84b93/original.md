```
restrict(ivref::GeneralVariableRef, supps...)::GeneralVariableRef
```

Restrict the input domain of an infinite variable/derivative `ivref` in  accordance with the infinite parameters and/or values `supps`. Here `supps` must  match the formatting of `ivref`'s infinite parameters. Here the following  outputs are possible:

  * Equivalent to `@variable(model, variable_type = Point(ivref, supps...)` if  `supps` are a complete support point
  * Equivalent to `@variable(model, variable_type = SemiInfinite(ivref, supps...)`  if `supps` are a partial support point.

Conveniently, we can also invoke this method by calling `ivref(supps...)`.

Errors if ivref is not an infinite variable or derivative or the formatting of  `supps` is incorrect. Will warn if `supps` only contain infinite parameters and  will simply return `ivref`.

**Example**

```julia-repl
julia> restrict(y, 0, x)
y(0, [x[1], x[2]])

julia> restrict(y, 0, [0, 0])
y(0, [0, 0])

julia> y(0, x)
y(0, [x[1], x[2]])

julia> y(0, [0, 0])
y(0, [0, 0])
```
