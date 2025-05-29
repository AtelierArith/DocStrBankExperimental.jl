```
eye(N::Int; type=Operator, dims=nothing)
qeye(N::Int; type=Operator, dims=nothing)
```

サイズ `N` の単位演算子 $\hat{\mathbb{1}}$。

異なるサブシステムが存在する場合は、ヒルベルト次元のリスト `dims` を指定することも可能です。

`type` は [`Operator`](@ref) または [`SuperOperator`](@ref) のいずれかでなければなりません。

!!! note
    `qeye` は `eye` の同義語です。

