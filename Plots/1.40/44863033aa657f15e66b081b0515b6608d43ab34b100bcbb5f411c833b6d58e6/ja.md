```
violin(x,y,z)
violin!(x,y,z)
```

バイオリンプロットを作成します。

# 例

```julia-repl
julia> violin(repeat([1,2,3],outer=100),randn(300))
```
