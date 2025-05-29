与えられたノートのためのキーと値のペアのリストを見つけます。結果は、フィールド `k` と `v` を持つ名前付きタプルのベクターです。

**例**

```juliarepl
julia> kvpairs(v, notenames[1])
3-element Vector{Any}:
 (k = "sequence", v = "16")
 (k = "hiddensequence", v = "16")
 Dict{Any, Any}()
```

```julia
kvpairs(v, note)

```
