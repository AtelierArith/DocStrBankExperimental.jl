```
wigner3j_f(::Type{T}, j₂, j₃, m₂, m₃) where {T<:Real}
```

Computes all allowed j₁ given fixed j₂, j₃, m₂, m₃, m₁=-m₂-m₃.

# Arguments

  * `T::Type{<:Real}`: output array type
  * `j₂`: quantum number
  * `j₃`: quantum number
  * `m₂`: quantum number
  * `m₃`: quantum number

# Returns

  * `Tuple{Vector{Int}, Vector{T}}`: j₁ values and wigner symbols
