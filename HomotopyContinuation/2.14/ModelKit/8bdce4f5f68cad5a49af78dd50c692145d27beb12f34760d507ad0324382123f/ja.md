```
taylor!(
    u,
    ::Val{K},
    H::CompiledHomotopy,
    x,
    p = nothing,
)
```

$$
u = H(x,t,p)
$$

のテイラー級数の次数$K$を計算します。
