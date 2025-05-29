```
indicatormat(x, c=sort(unique(x)); sparse=false)
```

ブール行列 `I` をサイズ `(length(c), length(x))` で構築します。`ci` を `x[i]` の `c` におけるインデックスとします。すると `I[ci, i] = true` となり、他のすべての要素は `false` になります。
