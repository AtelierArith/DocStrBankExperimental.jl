```
cumulant(x,n=get_order(x);simplify=true,kwargs...)
```

`x`の`n`番目の累積量を計算します（演算子または平均のいずれか）。出力は`simplify=true`のときに簡略化されます。さらに、キーワード引数は簡略化に渡されます。

# 例

```
julia> cumulant(a)
⟨a⟩

julia> cumulant(a*b)
(⟨a*b⟩+(-1*⟨a⟩*⟨b⟩))

julia> cumulant(a*b,1)
⟨a*b⟩

julia> cumulant(a*b,3)
0
```
