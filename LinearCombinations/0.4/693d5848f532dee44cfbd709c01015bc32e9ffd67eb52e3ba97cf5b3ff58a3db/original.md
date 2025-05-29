```
DenseLinear{T,R} <: AbstractLinear{T,R}

DenseLinear{T,R}(itr; basis::Basis)
```

Construct a linear combination of type `DenseLinear` with term type `T` and coefficient type `R` out of the term-coefficient pairs provided by the iterator `itr`.

Linear combinations of this type are internally stored as a `Vector` (or, more generally, an `AbstractArray`). The mandatory keyword argument `basis` is used to translate between terms and entries of the `Vector` (or `Array`). Operations involving two `DenseLinear` elements are much faster when the two bases are identical (in the sense of `===`).

Other ways to use this constructor are discussed under `AbstractLinear`.

See also [`Basis`](@ref), [`AbstractLinear`](@ref), [`Linear`](@ref), [`Linear1`](@ref), [`basis`](@ref), [`coordinates`](@ref).

# Examples

```jldoctest
julia> azbasis = Basis('a':'z')
Basis('a':1:'z')

julia> a = DenseLinear('x' => 1, 'y' => 2; basis = azbasis)
DenseLinear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> a + 'z'
DenseLinear{Char, Int64} with 3 terms:
'x'+2*'y'+'z'

julia> a + 'X'
ERROR: KeyError: key 'X' not found
[...]

julia> b = DenseLinear('x' => -1, 'z' => 3; basis = azbasis)
DenseLinear{Char, Int64} with 2 terms:
-'x'+3*'z'

julia> a + b
Linear{Char, Int64} with 2 terms:
2*'y'+3*'z'

julia> c = DenseLinear('a' => 5; basis = Basis('a':'c'))
DenseLinear{Char, Int64} with 1 term:
5*'a'

julia> add!(a, c)
DenseLinear{Char, Int64} with 3 terms:
5*'a'+'x'+2*'y'

julia> add!(c, a)
ERROR: KeyError: key 'x' not found
```
