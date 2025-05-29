```
strictly_upper_triangular_matrix(L::AbstractVector{T}) where {T <: NCRingElement}
```

主対角線の上にある要素が `L` の要素であり、それ以外はゼロである $n$ by $n$ 行列を返します。$n$ の値は、`L` の長さが $(n-1)n/2$ であるという条件によって決まります。

この性質を持つ整数 $n$ が存在しない場合は例外がスローされます。

# 例

```jldoctest
julia> strictly_upper_triangular_matrix([1, 2, 3])
[0   1   2]
[0   0   3]
[0   0   0]
```
