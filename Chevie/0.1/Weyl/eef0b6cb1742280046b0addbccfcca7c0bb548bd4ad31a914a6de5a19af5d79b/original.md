`badprimes(W)`

Let  `W`  be  a  Weyl  group.  A  prime  is  *bad*  for `W` if it divides a coefficient  of some  root on  the simple  roots. The  function `badprimes` returns the list of primes which are bad for `W`.

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> badprimes(W)
3-element Vector{Int64}:
 2
 3
 5
```
