```
between(p1::Point, p2::Point, r:range)
between(p1::Point, p2::Point, a:array)
```

点 `p1` と点 `p2` の間のポイントの配列を、範囲 `r` または配列 `a` のすべての `x` に対して返します。

`x` が 0.0 の場合、そのポイントは `p1` にあります。`x` が 1.0 の場合、そのポイントは `p2` にあります。

`x` が 0.5 の場合、そのポイントは `p1` と `p2` の中点です。
