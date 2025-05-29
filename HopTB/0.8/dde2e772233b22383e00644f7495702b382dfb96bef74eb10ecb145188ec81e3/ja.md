```julia
getspin(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Real})
```

`k` 点で ⟨n|σα|m⟩ を計算します。

`tm` が TBModel の場合、関数は `tm.isspinful` が true であるかどうかを確認します。
