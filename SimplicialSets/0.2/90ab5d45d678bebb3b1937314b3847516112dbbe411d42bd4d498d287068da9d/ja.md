```
isdegenerate(surj::Surjection) -> Bool
```

射影が退化しているのは、隣接する値が等しい場合です。

# 例

```jldoctest
julia> isdegenerate(Surjection([1, 2, 1]))
false

julia> isdegenerate(Surjection([1, 1, 2]))
true
```
