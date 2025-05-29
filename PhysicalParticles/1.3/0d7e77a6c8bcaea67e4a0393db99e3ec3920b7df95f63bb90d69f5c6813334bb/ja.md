```
function average(data, symbol::Symbol)
```

配列または配列の辞書内の要素のフィールド `symbol` の平均

## 例

```jl
a = rand(PVector{Float64}, 5)
average(a, :x)
```
