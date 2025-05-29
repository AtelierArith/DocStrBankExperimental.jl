```
merge_into!(a::Vector{MerCount{M}}, b::Vector{MerCount{M}}) where {M<:AbstractMer}
```

ベクター `b` からの `MerCount` をベクター `a` にマージします。

!!! note
    これにより、入力ベクター `a` と `b` がソートされます。

