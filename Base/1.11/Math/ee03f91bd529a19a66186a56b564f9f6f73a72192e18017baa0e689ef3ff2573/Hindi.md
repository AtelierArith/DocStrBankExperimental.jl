```
sqrt(x)
```

Return $\sqrt{x}$.

[`DomainError`](@ref) के लिए नकारात्मक [`Real`](@ref) तर्कों के लिए फेंकता है। इसके बजाय जटिल नकारात्मक तर्कों का उपयोग करें। ध्यान दें कि `sqrt` का एक शाखा कट नकारात्मक वास्तविक धुरी के साथ है।

प्रीफिक्स ऑपरेटर `√` `sqrt` के समकक्ष है।

देखें: [`hypot`](@ref).

# उदाहरण

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError with -81.0:
NaN result for non-NaN input.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im शाखा कट के नीचे है
0.0 - 9.0im

julia> .√(1:4)
4-तत्व वाला Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
