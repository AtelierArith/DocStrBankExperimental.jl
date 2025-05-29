```
upper_triangular_matrix(L::AbstractVector{T}) where {T <: NCRingElement}
```

主対角線上およびその上にある要素が `L` の要素であり、それ以外の場所にはゼロがある $n$ x $n$ 行列を返します。$n$ の値は、`L` の長さが $n(n+1)/2$ であるという条件によって決まります。

この性質を持つ整数 $n$ が存在しない場合は例外がスローされます。

# 例

```jldoctest
julia> upper_triangular_matrix([1, 2, 3])
[1   2]
[0   3]
```
