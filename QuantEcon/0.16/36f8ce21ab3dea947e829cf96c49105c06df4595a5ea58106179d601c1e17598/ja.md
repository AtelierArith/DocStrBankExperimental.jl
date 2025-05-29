```
interp(grid::AbstractVector, function_vals::AbstractVector)
```

一次元の線形補間

##### 例

```julia
breaks = cumsum(0.1 .* rand(20))
vals = 0.1 .* sin.(breaks)
li = interp(breaks, vals)

# スカラーを渡すことができる関数として `li` を扱って補間を行う
li(0.2)

# ブロードキャスティングを使用して複数の点で評価する
li.([0.1, 0.2, 0.3])
```
