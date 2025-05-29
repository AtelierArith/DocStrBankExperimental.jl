```
d,n,V = measure(body::AbstractParametricBody,x,t)
```

時刻 `t` における点 `x` に最も近い体の幾何学的特性を決定します。`dot(curve)` と `dot(map)` の両方が定義されている場合、`V` に寄与します。
