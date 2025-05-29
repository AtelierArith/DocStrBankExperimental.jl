```
RandomThinning(p)
```

保持確率 `p` によるランダムスリム。`p` は `[0,1]` の範囲の定数確率値または点を確率にマッピングする関数である可能性があります。

## 例

```julia
RandomThinning(0.5)
RandomThinning(p -> sum(to(p)))
```
