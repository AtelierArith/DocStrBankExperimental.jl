```
PeriodicArray{T,N} <: AbstractArray{T,N}
```

周期境界条件を持つ配列ラッパー。

# フィールド

  * `data::Array{T,N}`: 配列のデータ

# 例

```jldoctest
A = PeriodicArray([1, 2, 3])
A[0], A[2], A[4]

# 出力

(3, 2, 1)
```

```jldoctest
A = PeriodicArray([1 2; 3 4])
A[-1, 1], A[1, 1], A[4, 5]

# 出力

(1, 1, 3)
```

参照してください [`PeriodicVector`](@ref), [`PeriodicMatrix`](@ref)
