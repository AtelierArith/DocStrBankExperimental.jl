```
RawString(s::AbstractString)
```

Asymptote描画コマンドを直接挿入するためのコンテナ

# 例

```julia-repl
julia> Plot([Circle((0,0),1),RawString2D("draw((0,0)--dir(20));")])
```
