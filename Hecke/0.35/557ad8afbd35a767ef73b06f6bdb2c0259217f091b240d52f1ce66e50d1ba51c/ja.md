```
 can_solve_with_solution(f::QuadBin, n::IntegerUnion)
                                       -> Bool, Tuple{ZZRingElem, ZZRingElem}
```

負の判別式を持つ二次形式 `f` と整数 `n` に対して、整数 `x`、`y` が存在する場合は、$f(x, y) = n$ であるときにタプル `(true, (x, y))` を返します。該当する整数が存在しない場合は、`(false, (0, 0))` を返します。
