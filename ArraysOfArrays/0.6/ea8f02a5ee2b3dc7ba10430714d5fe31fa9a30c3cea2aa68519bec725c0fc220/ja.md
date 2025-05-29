```
flatview(A::AbstractArray)
flatview(A::AbstractArray{<:AbstractArray{<:...}})
```

配列 `A` を適切なフラットな形で表示します。フラットな形の形状は `A` の型によって異なります。`A` がネストされた配列でない場合、返される値は `A` 自身です。型特有のメソッドが利用できない場合、`flatview` は `Base.Iterators.flatten` にフォールバックします。
