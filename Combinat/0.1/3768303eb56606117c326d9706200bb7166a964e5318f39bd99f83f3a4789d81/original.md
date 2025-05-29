`moebius(n::Integer)`

The  classical  Möbius  function  is  the  Möbius  function of the poset of integers for divisibility. It is zero outside square-free integers, and for square-free integers is `(-1)ⁿ' where n is the number of prime factors.

```julia-repl
julia> moebius.(1:6)
6-element Vector{Int64}:
  1
 -1
 -1
  0
 -1
  1
```
