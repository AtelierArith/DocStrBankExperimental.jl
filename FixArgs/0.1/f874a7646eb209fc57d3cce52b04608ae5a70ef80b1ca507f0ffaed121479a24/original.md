The types produced by this package are unwieldly. This macro permits a convenient syntax, e.g. `@xquoteT func(::Arg1Type, ::Arg2Type)` to represent types.

```jldoctest
let func = identity, arg = 1
    typeof(@xquote func(arg)) == @xquoteT func(::typeof(arg))
end

# output

true
```

If an argument is "static", then it is part of the type, and the value is annotated as illustrated:

```julia
julia> @xquoteT string(123::::S)
FixArgs.Call{Some{typeof(string)},FrankenTuples.FrankenTuple{Tuple{Val{123}},(),Tuple{}}}
```
