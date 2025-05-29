```
between(p1::Point, p2::Point, x)
between((p1::Point, p2::Point), x)
```

点 `p1` と点 `p2` の間の点を `x` に対して見つけます。ここで `x` は通常 0 と 1 の間です。`between(p1, p2, 0.5)` は `midpoint(p1, p2)` と同等です。
