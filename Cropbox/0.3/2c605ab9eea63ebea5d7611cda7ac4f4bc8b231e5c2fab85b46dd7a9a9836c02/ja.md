```
plot(v::Number; kind, <keyword arguments>) -> Plot
plot(V::Vector; kind, <keyword arguments>) -> Plot
```

`kind` に応じて水平線または垂直線のグラフをプロットします。`kind` は `:hline` または `:vline` のいずれかです。初期の `hline` プロットには `xlim` が必要で、`vline` にはそれぞれ `ylim` が必要です。

参照: [`plot!`](@ref), [`visualize`](@ref)
