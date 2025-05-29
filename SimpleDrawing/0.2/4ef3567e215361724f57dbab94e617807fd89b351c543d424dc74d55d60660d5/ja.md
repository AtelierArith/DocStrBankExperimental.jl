```
my_spy(A::Matrix{T}, borders::Bool = false) where {T<:Number}
```

`my_spy(A::Matrix)` は、ゼロが白い四角形で、非ゼロが黒い四角形である `A` の白黒画像を作成します。
