```
crown(n::Integer, k::Integer)::Poset{Int}
```

Create the crown poset `S(n,k)`. This is a height-`2` poset  with `2n` vertices with elements `1` through `n` as minimals and  `n+1` through `2n` as maximals. Minimal element `a` is below exactly `n-k` maximals. Element `a` is *not* below elements `n+(a)` through `n+(a+k-1)` where the terms in parentheses wrap modulo `n`. 

For example, in `crown(5,2)` element `2` is not below `7` or `8`, but  `2<9`, `2<10`, and `2<6`.
