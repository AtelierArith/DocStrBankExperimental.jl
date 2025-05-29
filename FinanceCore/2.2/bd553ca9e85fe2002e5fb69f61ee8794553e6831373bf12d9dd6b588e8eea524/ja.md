```
discount(rate, t)
discount(rate, from, to)
```

時間`t`または区間`(from, to)`に対する`rate`の割引。`rate`が`Rate`でない場合、`Periodic`レートが1期間ごとに1回複利計算されるものと見なされます。すなわち、`Periodic(rate,1)`です。

# 例

```julia-repl
julia> discount(0.03, 10)
0.7440939148967249

julia> discount(Periodic(0.03, 2), 10)
0.7424704182237725

julia> discount(Continuous(0.03), 10)
0.7408182206817179

julia> discount(0.03, 5, 10)
0.8626087843841639
```
