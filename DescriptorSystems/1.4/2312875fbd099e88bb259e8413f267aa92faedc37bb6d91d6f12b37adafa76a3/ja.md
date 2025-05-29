```
 sysdiag = dsdiag(sys, k)
```

与えられた記述子システム `sys` と非負整数 `k` に対して、`sysdiag` を `sysdiag = diag( sys, ..., sys )` として得られる記述子システムを構築します（すなわち、`append` の `k` 回の繰り返し適用）。
