```
@widen(typetag, types)
```

Expand the set of types corresponding to a type tag to include `types`, where `types` is either a single type or any collection that may be passed to a set constructor.  A type tag is a module-qualified symbol `mod.:Key` where mod specifies a module and `:Key` is a symbol.  If just the `:Key` is given, then the module is assumed to be the module in which the macro was expanded.  If no concretization exists, create a default concretization consisting of the conrete subtypes of whatever type shares the name of `Key` at load time.

If `@widen` is called for a type tag which has been referenced by a `@replicable` code block, then that code block will be replicated even more to reflect the new concretization.

# Examples

```julia-repl
julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @replicable println(@hyperspecialize(BestInts))
Int32
Int64

julia> @widen BestInts (Bool, Int32, UInt128)
Bool
UInt128
Set(Type[Bool, UInt128, Int32, Int64])

julia> @concretization BestInts
Set(Type[Bool, Int8, Int32, Int64, UInt128])
```
