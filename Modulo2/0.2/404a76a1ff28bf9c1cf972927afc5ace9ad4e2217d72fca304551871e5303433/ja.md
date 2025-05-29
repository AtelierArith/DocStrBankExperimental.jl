```
ZZ2Vector <: AbstractVector{ZZ2}
ZZ2Matrix <: AbstractMatrix{ZZ2}
ZZ2Array{N} <: AbstractArray{ZZ2,N}
```

要素の型が `ZZ2` の抽象ベクトル / 行列 / 配列タイプ。

内部表現はパックされており、各要素は1ビットのみを使用します。ただし、列は内部的に256の倍数の長さにパディングされます。

`ZZ2Array` は、要素を `ZZ2` に変換できる任意の `AbstractArray` から作成できます。また、`undef` 引数を使用して要素を未定義のままにすることもできます。

他にも [`zeros`](@ref)、[`ones`](@ref)、[`zz2vector`](@ref)、[`resize!`](@ref)、[`det`](@ref)、[`inv`](@ref)、[`rank`](@ref)、[`rcef`](@ref)、[`rref`](@ref) を参照してください。

# 例

```jldoctest
julia> ZZ2Matrix([1 2 3; 4 5 6])
2×3 ZZ2Matrix:
 1  0  1
 0  1  0

julia> v = ZZ2Vector(undef, 2); v[1] = true; v[2] = 2.0; v
2-element ZZ2Vector:
 1
 0
```
