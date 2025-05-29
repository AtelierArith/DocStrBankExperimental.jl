```julia
maximumrotation(s)

```

与えられた文字列/ベクトルのすべての回転の最大値を見つけます。

例えば、文字列 `aab` には3つの回転があります: `aab`, `aba`, `baa` であり、`baa` が最大の回転です。

```jldoctest
julia> maximumrotation("aab")
"baa"
```
