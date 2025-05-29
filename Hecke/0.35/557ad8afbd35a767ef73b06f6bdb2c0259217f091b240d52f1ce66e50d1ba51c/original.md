```
 can_solve_with_solution(f::QuadBin, n::IntegerUnion)
                                       -> Bool, Tuple{ZZRingElem, ZZRingElem}
```

For a binary quadratic form `f` with negative discriminant and an integer `n`, return the tuple `(true, (x, y))` if $f(x, y) = n$ for integers `x`, `y`. If no such integers exist, return `(false, (0, 0))`
