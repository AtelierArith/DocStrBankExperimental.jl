```
evaluate(a::FreeAssociativeAlgebraElem{T}, vals::Vector{U}) where {T <: RingElement, U <: NCRingElem}
```

`a`を各変数の値の配列で置き換えて評価します。評価は、`a`の係数環の要素と`vals`の要素の間で乗算が定義されている場合に成功します。

構文`a(vals...)`もサポートされています。

# 例

```jldoctest
julia> R, (x, y) = free_associative_algebra(ZZ, ["x", "y"]);

julia> f = x*y - y*x
x*y - y*x

julia> S = matrix_ring(ZZ, 2);

julia> m1 = S([1 2; 3 4])
[1   2]
[3   4]

julia> m2 = S([0 1; 1 0])
[0   1]
[1   0]

julia> evaluate(f, [m1, m2])
[-1   -3]
[ 3    1]

julia> m1*m2 - m2*m1 == evaluate(f, [m1, m2])
true

julia> m1*m2 - m2*m1 == f(m1, m2)
true
```
