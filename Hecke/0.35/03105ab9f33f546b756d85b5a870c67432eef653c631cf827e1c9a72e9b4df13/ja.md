```
is_primitive(L::ZZLat, v::Union{Vector, QQMatrix}) -> Bool
```

ベクトル `v` が `L` において原始的であるかどうかを返します。

$$
\mathbb Z
$$

-格子 `L` におけるベクトル `v` は、すべての `L` の `w` に対して $v = dw$ となる整数 `d` が存在する場合、`d = \pm 1` であるときに原始的であると呼ばれます。
