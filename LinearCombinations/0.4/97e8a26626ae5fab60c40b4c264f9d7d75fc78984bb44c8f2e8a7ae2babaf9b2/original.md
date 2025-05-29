```
coordinates(a::DenseLinear{T,R}) -> AbstractArray{R}
```

Return the coordinates of `a` with respect to the basis used for it. The coordinate array (usually a vector) has the same axes as the basis. Modifying this array will also modify `a`.

See also [`basis`](@ref).

# Example

```jldoctest
julia> b = Basis('x':'z')
Basis('x':1:'z')

julia> a = DenseLinear('x' => 1, 'z' => 2; basis = b)
DenseLinear{Char, Int64} with 2 terms:
'x'+2*'z'

julia> v = coordinates(a)
3-element Vector{Int64}:
 1
 0
 2

julia> a == Linear(x => c for (x, c) in zip(basis(a), v))
true

julia> v[2] = -1; a
DenseLinear{Char, Int64} with 3 terms:
'x'-'y'+2*'z'
```
