```
@interpret [interp] f(args; kwargs...)
```

Evaluate `f` on the specified arguments using the interpreter.

# Example

```jldoctest
julia> a = [1, 7];

julia> sum(a)
8

julia> @interpret sum(a)
8
```
