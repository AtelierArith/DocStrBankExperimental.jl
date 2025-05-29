```
@do Monad block
Monad.@do block
```

do notation for monads. a.k.a. computation expressions.

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> result = Maybe.@do begin
           a ← Some(1)
           b ← Some(2)
           return a + b
       end
Some(3)
```
