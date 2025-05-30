```
findall(c::AbstractChar, s::AbstractString)
```

ベクトル `I` を返します。これは `s` の中で `s[i] == c` となるインデックスです。`s` にそのような要素がない場合は、空の配列を返します。

# 例

```jldoctest
julia> findall('a', "batman")
2-element Vector{Int64}:
 2
 5
```

!!! compat "Julia 1.7"
    このメソッドは少なくとも Julia 1.7 が必要です。

