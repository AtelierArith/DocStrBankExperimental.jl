```
@concretize(typetag, types)
```

Define the set of types corresponding to a type tag as `types`, where `types` is either a single type or any collection that may be passed to a set constructor.  A type tag is a module-qualified symbol `mod.:Key` where mod specifies a module and `:Key` is a symbol.  If just the `:Key` is given, then the module is assumed to be the module in which the macro was expanded.

Note that you may not concretize a type in another module.

# Examples

```julia-repl
julia> @concretize Main.BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @concretize BestFloats Float64
Set(Type[Float64])

julia> @concretize BestStrings (String,)
Set(Type[String])

julia> @concretization BestInts
Set(Type[Int32, Int64])
```
