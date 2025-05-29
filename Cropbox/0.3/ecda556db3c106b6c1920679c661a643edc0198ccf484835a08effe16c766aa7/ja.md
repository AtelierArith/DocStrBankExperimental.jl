```
plot(df::DataFrame, x, y; <keyword arguments>) -> Plot
plot(X::Vector, Y::Vector; <keyword arguments>) -> Plot
plot(df::DataFrame, x, y, z; <keyword arguments>) -> Plot
```

提供されたデータソースからグラフをプロットします。グラフの種類は引数に基づいて選択されます。

参照: [`plot!`](@ref), [`visualize`](@ref)
