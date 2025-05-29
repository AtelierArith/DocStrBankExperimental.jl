ファイル `f` からキーと値のペアのリストを抽出します。結果は、`k` と `v` の2つのフィールドを持つ名前付きタプルのベクターです。

**例**

```juliarepl
julia> kvpairs("/path/to/file.md")
3-element Vector{Any}:
 (k = "sequence", v = "16")
 (k = "hiddensequence", v = "16")
 Dict{Any, Any}()
```

```julia
kvpairs(f)

```
