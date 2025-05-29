```
spread(curve1,curve2,cashflows)
```

`curve1`に加えるべき定数スプレッドを返し、割引された`cashflows`を`curve2`と等しくします。

# 例

```julia-repl
spread(0.04, 0.05, cfs)
Rate{Float64, Periodic}(0.010000000000000009, Periodic(1))
```
