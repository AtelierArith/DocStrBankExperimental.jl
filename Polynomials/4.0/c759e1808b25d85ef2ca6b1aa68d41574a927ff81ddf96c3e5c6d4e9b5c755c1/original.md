```
residues(pq::AbstractRationalFunction; method=:numerical,  kwargs...)
```

If `p/q =d + r/q`, returns `d` and the residues of a rational fraction `r/q`.

First expresses `p/q =d + r/q` with `r` of lower degree than `q` through `divrem`. Then finds the poles of `r/q`. For a pole, `λj` of multiplicity `k` there are `k` residues, `rⱼ[k]/(z-λⱼ)^k`, `rⱼ[k-1]/(z-λⱼ)^(k-1)`, `rⱼ[k-2]/(z-λⱼ)^(k-2)`, …, `rⱼ[1]/(z-λⱼ)`. The residues are found using this formula: `1/j! * dʲ/dsʲ (F(s)(s - λⱼ)^k` evaluated at `λⱼ` ([5-28](https://stanford.edu/~boyd/ee102/rational.pdf)).

## Example

(From page 5-33 of above pdf)

```jldoctest rational_functions
julia> using Polynomials


julia> s = variable(Polynomial, :s)
Polynomial(1.0*s)

julia> pq = (-s^2 + s + 1) // ((s-1) * (s+1)^2)
(1.0 + 1.0*s - 1.0*s^2) // (-1.0 - 1.0*s + 1.0*s^2 + 1.0*s^3)

julia> d,r = residues(pq);


julia> d
Polynomial(0.0)

julia> r
Dict{Float64, Vector{Float64}} with 2 entries:
  -1.0 => [-1.25, 0.5]
  1.0  => [0.25]

julia> iszero(d)
true

julia> z = variable(pq)
(1.0*s) // (1.0)

julia> for (λ, rs) ∈ r # reconstruct p/q from output of `residues`
           for (i,rᵢ) ∈ enumerate(rs)
               d += rᵢ/(z-λ)^i
           end
       end


julia> p′, q′ = lowest_terms(d);


julia> q′ ≈ (s-1) * (s+1)^2 # works, as q is monic
true

julia> p′ ≈ (-s^2 + s + 1)
true
```

!!! note
    There are several areas where numerical issues can arise. The `divrem`, the identification of multiple roots (`multroot`), the evaluation of the derivatives, ...

