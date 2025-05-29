```
present_values(interest, cashflows, timepoints)
```

与えられたキャッシュフローの各期間における現在価値を表すベクトルを効率的に計算します。

# 例

```julia-repl
julia> present_values(0.00, [1,1,1])
[3,2,1]

julia> present_values(ForwardYield([0.1,0.2]), [10,20],[0,1]) # `using FinanceModels` の後
2-element Vector{Float64}:
 28.18181818181818
 18.18181818181818
```
