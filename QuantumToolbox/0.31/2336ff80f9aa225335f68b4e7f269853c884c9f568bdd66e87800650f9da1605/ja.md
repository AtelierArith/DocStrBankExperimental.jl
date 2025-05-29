```
A ⋅ B
dot(A::QuantumObject, B::QuantumObject)
```

2つの [`QuantumObject`](@ref) の間の内積を計算します: $\langle A | B \rangle$

`A` と `B` は [`Ket`](@ref) または [`OperatorKet`](@ref) である必要があります。

!!! note
    `A ⋅ B`（ここで `⋅` は REPL で `\cdot` をタブ補完することで入力できます）は `dot(A, B)` の同義語です。

