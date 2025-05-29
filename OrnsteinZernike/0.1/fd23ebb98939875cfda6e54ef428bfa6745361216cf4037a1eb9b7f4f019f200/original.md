```
compute_virial_pressure(sol::OZSolution, system::SimpleLiquid)
```

Computes the pressure via the virial route

uses the formula p = kBTρ - 1/(2d) ρ^2 ∫dr r g(r) u'(r) for single component systems and p =  kBT Σᵢρᵢ - 1/(2d) Σᵢⱼ ρᵢρⱼ ∫dr r gᵢⱼ(r) u'ᵢⱼ(r) for mixtures.

It handles discontinuities in the interaction potential analytically if `discontinuities(potential)` is defined. For additional speed/accuracy define a method of `evaluate_potential_derivative(potential, r::Number)` that analytically computes du/dr.  By default this is done using finite differences.
