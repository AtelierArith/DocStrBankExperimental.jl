```
fcialg(n::V, I, par...; augmented=true, verbose=false, kwargs...)
```

変数 `n` のセットに対して FCI アルゴリズムを実行します。

```
I(u, v, [s1, ..., sn], par...)
```

PAG を MetaDiGraph として返します。
