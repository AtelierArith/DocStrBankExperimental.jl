```
Section(A::Float64, E::Float64, G::Float64, Ix::Float64, Iy::Float64, J::Float64, ρ::Float64 = 1.)
Section(mat::Material, A::Float64, Ix::Float64, Iy::Float64, J::Float64)
```

A cross section assigned to an element.

# Fields

  * `A` Area [Distance²]
  * `E` Modulus of Elasticity [Force/Distance²]
  * `Ix` Nominal strong moment of inertia [Distance⁴]
  * `Iy` Nominal weak moment of inertia [Distance⁴]
  * `J` Torsional constant [Distance⁴]
  * `ρ=1` Density [Mass/Distance³]
