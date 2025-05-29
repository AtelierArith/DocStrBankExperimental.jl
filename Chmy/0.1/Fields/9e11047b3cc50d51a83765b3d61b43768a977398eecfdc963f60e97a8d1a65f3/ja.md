```
abstract type AbstractField{T,N,L} <: AbstractArray{T,N}
```

データ型 `T`、次元数 `N`、フィールドが定義される場所 `L` を持つフィールドを表す抽象型です。

参照: 抽象型 [`ConstantField`](@ref)
