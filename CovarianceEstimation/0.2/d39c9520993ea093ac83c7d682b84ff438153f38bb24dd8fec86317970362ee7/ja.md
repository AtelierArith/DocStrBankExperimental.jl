```
LinearShrinkage(target, shrinkage; corrected=false, drop_var0=false)
```

線形収縮推定量は、式 $(1 - \lambda) S + \lambda F$ によって説明され、ここで $S$ は標準共分散行列、$F$ は引数 `target` によって説明される収縮ターゲット、$\lambda$ は収縮パラメータであり、`shrinkage` で明示的に与えられるか、サポートされている方法のいずれかに従って自動的に決定されます。

`corrected` が true の場合、修正された推定量が使用されます。`drop_var0=true` は、$\lambda$ の計算からゼロ分散変数を除外します。
