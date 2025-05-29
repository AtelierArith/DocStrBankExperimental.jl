```julia
minimumrotation(s)

```

与えられた文字列/ベクトルのすべての回転の最小値を見つけます。

例えば、文字列 `aab` には3つの回転があります: `aab`, `aba`, `baa` であり、`aab` が最小の回転です。

```jldoctest
julia> minimumrotation("aab")
"aab"
```
