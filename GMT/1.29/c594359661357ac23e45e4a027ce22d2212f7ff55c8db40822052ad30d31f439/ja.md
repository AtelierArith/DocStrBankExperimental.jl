```
ecdfplot(x::AbstractVector{<:Real}; kwargs...)
```

`x`の経験的累積分布関数（ECDF）をプロットします。`kwargs`には`plot`モジュールで使用される任意のオプションを含めることができます。

例:     ecdfplot(randn(100), show=true)
