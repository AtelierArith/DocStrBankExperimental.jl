```
@concretization(typetag)
```

Return the set of types corresponding to a type tag.  A type tag is a module-qualified symbol `mod.:Key` where mod specifies a module and `:Key` is a symbol.  If just the `:Key` is given, then the module is assumed to be the module in which the macro was expanded.  If no concretization exists, return nothing.

A concretization can be set and modified with `@concretize` and `@widen`

# Examples

```julia-repl
julia> @concretization(BestInts)
nothing

julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @concretization BestInts
Set(Type[Int32, Int64])
```
