```
evaluate(a::FreeAssociativeAlgebraElem{T}, vals::Vector{U}) where {T <: RingElement, U <: NCRingElem}
```

Evaluate `a` by substituting in the array of values for each of the variables. The evaluation will succeed if multiplication is defined between elements of the coefficient ring of `a` and elements of `vals`.

The syntax `a(vals...)` is also supported.

# Examples

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
