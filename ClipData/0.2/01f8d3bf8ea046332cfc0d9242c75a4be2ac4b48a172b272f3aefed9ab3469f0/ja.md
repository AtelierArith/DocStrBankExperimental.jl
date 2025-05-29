```
cliptable(t; delim = '	', kwargs...)
```

Tables.jl互換のオブジェクトをクリップボードに送信します。デフォルトの区切り文字はタブです。`CSV.write`に渡すことができるすべてのキーワード引数を受け付けます。

# 例

```julia-repl
julia> t = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> cliptable(t)
a   b
1   100
2   200
3   300
```
