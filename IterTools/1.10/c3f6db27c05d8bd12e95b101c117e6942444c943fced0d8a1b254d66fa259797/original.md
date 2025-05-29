```
interleaveby(predicate=Base.isless, a, b)
```

Iterate over the an interleaving of `a` and `b` selected by the predicate (default less-than).

Input:

  * `predicate(ak,bk) -> Bool`:  Whether to pick the next element of `a` (true) or `b` (false).
  * `fa(ak)`, `fb(bk)`: Functions to apply to the picked elements

```jldoctest
julia> collect(interleaveby(1:2:5, 2:2:6))
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

If the predicate is `Base.isless` (the default) and both inputs are sorted, this produces the sorted output. If the predicate is a stateful functor that alternates true-false-true-false... then this produces the classic interleave operation as described e.g. in the definition of microkanren.
