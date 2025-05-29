```
isurl(str)
```

与えられた文字列が絶対URLであるかどうかをチェックします。

# 例

```julia-repl
julia> isurl("https://julialang.org")
true
julia> isurl("mailto:someone@example.com")
true
julia> isurl("/foo/bar")
false
```
