```
add_dotcalls(::Type{DottedT}, dotcalllist)
```

Add the properties in `dotcalllist` to the list of properties that can be dot-called for a type `DottedT` that has already been DotCall-ified.

Only properties that are not already DotCall-ified for `DottedT` are added. Previous added properties will not be updated.

Since `add_dotcalls` is a function, in contrast to `@dotcallify`, `dotcalllist` can be a literal container (for example `Tuple` or `Vector`) or a variable name bound to a container.

Returns a `Vector` of two-tuples (`Tuple`) of the properties that were added, that is, not already on the list.

# Examples

```julia-repl
julia> dotcallified_properties(MyA)
(sx = MyAs.sx, x = MyAs.x, sin = sin, y = 3, mycos = MyAs.var"#1#3"())

julia> add_dotcalls(MyA, (:x, :sx, :cf))
1-element Vector{Tuple{Symbol, Symbol}}:
 (:cf, :cf)

julia> add_dotcalls(MyA, (:x, :sx, :cf))
()
```
