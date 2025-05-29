```
term(x)
```

Wrap argument in an appropriate `AbstractTerm` type: `Symbol`s and `AbstractString`s become `Term`s, and `Number`s become `ConstantTerm`s.  Any `AbstractTerm`s are unchanged. `AbstractString`s are converted to symbols before wrapping.

# Example

```jldoctest
julia> ts = term.((1, :a, "b"))
1
a(unknown)
b(unknown)

julia> typeof(ts)
Tuple{ConstantTerm{Int64}, Term, Term}
```
