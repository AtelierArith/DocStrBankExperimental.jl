```
RandomThinning(p)
```

保持確率 `p` によるランダムスリムニング。`p` は `[0,1]` の範囲の定数確率値または点を確率にマッピングする関数であることができます。

## 例

```julia
RandomThinning(0.5)
RandomThinning(p -> sum(coordinates(p)))
```
