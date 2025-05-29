`Pol(p::Mvp{T}) where T`

converts the one-variable `Mvp{T}` `p` to a `Pol{T}`. It is an error if `p` has  more  than  one  variable,  or  this  variable appears to non-integral powers.

```julia-repl
julia> @Mvp x; @Pol q; Pol(x^2+x)
Pol{Int64}: q²+q
```
