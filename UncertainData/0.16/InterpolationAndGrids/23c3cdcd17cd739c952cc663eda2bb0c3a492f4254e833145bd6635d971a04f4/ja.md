```
bin!(bins::Vector{AbstractVector{T}}, left_bin_edges::AbstractRange{T}, xs, ys) where T
```

`ys`の要素を、`left_bin_edges`の`N`グリッドポイントによって定義されたビンに基づいて、`N-1`の異なる事前割り当てされた空のビンベクターに分配します。`bins`は、ベクターのような可変コンテナのベクターでなければなりません。

`xs[i]`が`n`番目のビン区間に入る場合、`ys[i]`は`n`番目のビンベクターに割り当てられます。`xs[i]`がグリッドの外にある場合、対応する`ys[i]`は無視されます。

[`bin(::AbstractRange)`](@ref)も参照してください。
