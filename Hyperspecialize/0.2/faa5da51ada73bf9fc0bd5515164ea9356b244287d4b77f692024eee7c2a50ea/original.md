```
@replicable block
```

Replicate the code in `block` where each type tag referred to by `@hyperspecialize(typetag)` is replaced by an element in the concretization of `typetag`.  `block` is replicated at global scope in the module where `@replicable` was expanded once for each combination of types in the concretization of each `typetag`.  A type tag is a module-qualified symbol `mod.:Key` where mod specifies a module and `:Key` is a symbol.  If just the `:Key` is given, then the module is assumed to be the module in which the macro was expanded.  If no concretization exists for a type tag, create a default concretization consisting of the conrete subtypes of whatever type shares the name of `Key` at load time.

If `@widen` is called for a type tag which has been referenced by a `@replicable` code block, then that code block will be replicated even more to reflect the new concretization.

# Examples

```julia-repl
julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @replicable println(@hyperspecialize(BestInts), @hyperspecialize(BestInts))
Int32Int32
Int32Int64
Int64Int32
Int64Int64

julia> @widen BestInts (Bool,)
BoolBool
BoolInt32
BoolInt64
Int32Bool
Int64Bool
Set(Type[Bool, Int32, Int64])
```
