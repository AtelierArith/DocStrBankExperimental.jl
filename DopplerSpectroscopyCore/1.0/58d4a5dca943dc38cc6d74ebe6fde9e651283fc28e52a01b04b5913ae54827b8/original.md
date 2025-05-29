```
probe(δ::Real, two_level, light) -> Real
probe(δ_vec::Vector{T}, two_level, light) -> Vector{T} where T<:Real
probe(δ_range::LinRange{T1, T2}, two_level, light)
-> Vector{T1} where {T1<:Real, T2<:Integer}
```

Compute probability `nₑ` of a quantum system to be in excited state for detuning `δ`. By supplying multiple detuning values via `δ_vec` or `δ_range` compute `nₑ` for each of them.

# Arguments

  * `δ` :
  * `two_level::Quantum2Level` :
  * `light::LightSource` :

# Returns

  * `nₑ` :   Real number.

# See also

  * [`StateVector`](@ref)

# References

  * Springer: https://link.springer.com/chapter/10.1007/978-1-4684-4550-3_5   (If you find any unpaywalled refence, please contact me via mail suggested on package's   github page or create an issue)
