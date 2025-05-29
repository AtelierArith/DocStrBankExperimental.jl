```
BetaZ(beta::T) where {T<:Real}
```

Represents the beta parameter associated with a Lorentz boost along the z-axis, commonly denoted as $\beta_z$.

The transformation for a boost along the z-axis is:

$$
\begin{pmatrix}
p_0\\
p_1\\
p_2\\
p_3
\end{pmatrix} \mapsto
\begin{pmatrix}
\gamma (p_0 - \beta_z p_3)\\
p_1\\
p_2\\
\gamma (p_3 - \beta_z p_0)\\
\end{pmatrix}
$$

where the kinematic factor is given as $\gamma = 1/\sqrt{1-\beta_z^2}$)

## Example

```jldoctest
julia> using QEDcore

julia> using Random

julia> RNG = MersenneTwister(1234)
MersenneTwister(1234)

julia> beta_z = BetaZ(0.5)
BetaZ{Float64}(0.5)

julia> boost = Boost(beta_z)
Boost{BetaZ{Float64}}(BetaZ{Float64}(0.5))

julia> p = SFourMomentum(4,3,2,1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost(p)
4-element SFourMomentum with indices SOneTo(4):
  4.041451884327381
  3.0
  2.0
 -1.1547005383792517

julia> @assert isapprox(p*p,p_prime*p_prime) # Invariant mass is preserved

```

## External link

  * [Lorentz Boost on Wikipedia](https://en.wikipedia.org/wiki/Lorentz_transformation)
  * [Kinematics in PDG review](https://pdg.lbl.gov/2024/reviews/rpp2024-rev-kinematics.pdf)
