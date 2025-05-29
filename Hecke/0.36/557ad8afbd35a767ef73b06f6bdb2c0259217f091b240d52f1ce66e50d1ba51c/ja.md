```
 can_solve_with_solution(f::QuadBin, n::IntegerUnion)
                                       -> Bool, Tuple{ZZRingElem, ZZRingElem}
```

負の判別式を持つ二次形式 `f` と整数 `n` に対して、整数 `x`、`y` が存在し、$f(x, y) = n$ であればタプル `(true, (x, y))` を返します。そうでない場合は `(false, (0, 0))` を返します。
