```
size(A::AbstractQuantumObject)
size(A::AbstractQuantumObject, idx::Int)
shape(A::AbstractQuantumObject)
shape(A::AbstractQuantumObject, idx::Int)
```

[`AbstractQuantumObject`](@ref) の配列の各次元を含むタプルを返します。

オプションで、インデックス（`idx`）を指定すると、配列の対応する次元だけを取得できます。

!!! note
    `shape` は `size` の同義語です。

