```
path3d(x,y,z)
path3d!(x,y,z)
```

3Dパスを`(x[1],y[1],z[1])`から`(x[2],y[2],z[2])`、...、`(x[end],y[end],z[end])`までプロットします。

# 例

```julia-repl
julia> path3d([0,1,2,3],[0,1,4,9],[0,1,8,27])
```
