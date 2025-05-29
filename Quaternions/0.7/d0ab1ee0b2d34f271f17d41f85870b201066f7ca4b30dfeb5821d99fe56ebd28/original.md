```
imag_part(q::Quaternion{T}) -> NTuple{3, T}
```

Return the imaginary part of the quaternion `q`.

Note that this function is different from `Base.imag`, which returns `Real` for complex numbers.

See also: [`real`](@ref), [`conj`](@ref).

# Examples

```jldoctest
julia> imag_part(Quaternion(1,2,3,4))
(2, 3, 4)
```
