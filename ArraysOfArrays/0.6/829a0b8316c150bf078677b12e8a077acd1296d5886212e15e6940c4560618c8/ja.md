```
consgrouped_ptrs(A::AbstractVector)
```

等しい連続するエントリをグループ化することを示す `VectorOfVectors` の作成に適した要素ポインタベクターを計算します。

例:

```julia
    A = [1, 1, 2, 3, 3, 2, 2, 2]
    elem_ptr = consgrouped_ptrs(A)
    first.(VectorOfVectors(A, elem_ptr)) == [1, 2, 3, 2]
```

consgrouped*ptrs 通常、`elem*ptr` は計算されたグループ化を他のデータに適用するために使用されます:

```julia
    B = [1, 2, 3, 4, 5, 6, 7, 8]
    VectorOfVectors(B, elem_ptr) == [[1, 2], [3], [4, 5], [6, 7, 8]]
```
