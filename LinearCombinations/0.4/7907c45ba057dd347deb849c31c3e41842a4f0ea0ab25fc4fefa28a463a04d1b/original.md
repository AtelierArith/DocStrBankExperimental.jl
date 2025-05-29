```
Linear1{T,R} <: AbstractLinear{T,R}

Linear1{T,R}(itr)
```

Construct a linear combination of type `Linear1` with term type `T` and coefficient type `R` out of the term-coefficient pairs provided by the iterator `itr`.

Linear combinations of this type can hold at most one non-zero term-coefficient pair at any time. There are often situations where this is sufficient, and in these cases `Linear1` is much more efficient than `Linear` or `DenseLinear`.

Other ways to use this constructor are discussed under `AbstractLinear`.

See also [`AbstractLinear`](@ref), [`Linear`](@ref), [`DenseLinear`](@ref).

# Examples

```jldoctest
julia> a = Linear1('x' => 1)
Linear1{Char, Int64} with 1 term:
'x'

julia> add!(a, 'x')
Linear1{Char, Int64} with 1 term:
2*'x'

julia> addmul!(a, 'x', -2)
Linear1{Char, Int64} with 0 terms:
0

julia> a + 'y'   # works because a is zero
Linear1{Char, Int64} with 1 term:
'y'

julia> a + 'y' + 'z'
ERROR: Linear1 cannot store linear combinations of two or more elements
[...]

julia> a = Linear1('x' => 1); b = Linear1('y' => 2); a+b
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> typeof(ans)
Linear{Char, Int64}
```
