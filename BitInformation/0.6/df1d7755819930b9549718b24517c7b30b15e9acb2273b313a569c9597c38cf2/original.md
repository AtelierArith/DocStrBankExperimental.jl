```julia
B = signed_exponent(A::AbstractArray{T}) where {T<:Base.IEEEFloat}
```

Converts the exponent bits of Float16,Float32 or Float64-arrays from its IEEE standard biased-form into a sign-magnitude representation.

# Example

```julia
julia> bitstring(10f0,:split)
"0 10000010 01000000000000000000000"

julia> bitstring.(signed_exponent([10f0]),:split)[1]
"0 00000011 01000000000000000000000"
```

In the IEEE standard floats the exponent 3 is interpret from 0b10000010=130 via subtraction of the exponent bias of Float32 = 127. In sign-magnitude representation the exponent is inferred from the first exponent (0) as sign bit and a magnitude 2^1 + 2^1 = 3. NaN/Inf exponent bits are mapped to negative zero in sign-magnitude representation which is exactly reversed with `biased_exponent`.
