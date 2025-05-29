`Quadratic(c::Cyc)`

determines  if  `c`  lives  in  a  quadratic  extension  of  `ℚ`. The call `q=Quadratic(c)`  returns a  struct `Quadratic`  with fields  `q.a`, `q.b`, `q.root`,  `q.den` such that `c==(q.a + q.b root(q.root))//q.den` if such a representation is possible or returns `nothing` otherwise.

# Examples

```julia-repl
julia> Quadratic(E(3,2)-2E(3))
(1-3√-3)/2

julia> Quadratic(1+E(5))

```
