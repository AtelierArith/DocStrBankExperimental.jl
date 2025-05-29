```
BetaVector(x::Real,y::Real,z::Real)
```

Represents the spatial vector of velocity parameters (denoted as the "beta" vector) associated with motion in the three Cartesian directions, i.e., $\vec\beta = (\beta_x, \beta_y, \beta_z)$. These components correspond to the velocity of an object (in units of the speed of light) in each of the $x$, $y$, and $z$ directions.

The Lorentz boost along the direction of the beta vector $\vec\beta$ transforms the four-momentum as follows:

$$
\begin{pmatrix}
p_0\\
p_1\\
p_2\\
p_3
\end{pmatrix} \mapsto
\begin{pmatrix}
    \gamma  (p_0 - \vec\beta \vec p)\\
p_1 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_x\\
p_2 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_y\\
    p_3 + (\frac{\gamma - 1}{\beta^2} \vec\beta\vec p - \gamma  p_0)
 \beta_z\\
\end{pmatrix}
$$

where the kinematic factor is given as $\gamma = 1/\sqrt{1-\beta_x^2}$.

## Example

```jldoctest
julia> using QEDcore

julia> beta_vec = BetaVector(0.2,0.3,0.1)
BetaVector{Float64}(0.2, 0.3, 0.1)

julia> boost = Boost(beta_vec)
Boost{BetaVector{Float64}}(BetaVector{Float64}(0.2, 0.3, 0.1))

julia> p = SFourMomentum(4.0,3.0,2.0,1.0)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost(p)
4-element SFourMomentum with indices SOneTo(4):
 2.911484876492837
 2.282803602436349
 0.9242054036545237
 0.6414018012181746

julia> @assert isapprox(p*p,p_prime*p_prime) # Invariant mass is preserved
```

## External link

  * [Lorentz Boost on Wikipedia](https://en.wikipedia.org/wiki/Lorentz_transformation)
  * [Kinematics in PDG review](https://pdg.lbl.gov/2024/reviews/rpp2024-rev-kinematics.pdf)
  * [`ROOT::Math:Boost` from ROOT](https://root.cern.ch/doc/master/classROOT_1_1Math_1_1Boost.html)
