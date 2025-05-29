```
add_cboo_calls(::Type{CBOOedT}, cboolist)
```

Add the properties in `cboolist` to the list of properties that can be cboo-called for a type `CBOOedT` that has already been cboo-ified.

Only properties that are not already CBOO-ified for `CBooedT` are added. Previous added properties will not be updated.

Since `add_cboo_calls` is a function, in contrast to `@cbooify`, `cboolist` can be a literal container (for example `Tuple` or `Vector`) or a variable name bound to a container.

Returns a `Vector` of two-tuples (`Tuple`) of the properties that were added, that is, not already on the list.

# Examples

```julia-repl
julia> cbooified_properties(MyA)
(sx = MyAs.sx, x = MyAs.x, sin = sin, y = 3, mycos = MyAs.var"#1#3"())

julia> add_cboo_calls(MyA, (:x, :sx, :cf))
1-element Vector{Tuple{Symbol, Symbol}}:
 (:cf, :cf)

julia> add_cboo_calls(MyA, (:x, :sx, :cf))
()
```
