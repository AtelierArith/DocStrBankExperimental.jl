```
random_velocity(atom_mass::Union{Unitful.Mass, MolarMass}, temp::Unitful.Temperature;
                dims=3, rng=Random.default_rng())
random_velocity(atom_mass::Union{Unitful.Mass, MolarMass}, temp::Unitful.Temperature,
                k::Union{BoltzmannConstUnits, MolarBoltzmannConstUnits};
                dims=3, rng=Random.default_rng())
random_velocity(atom_mass::Real, temp::Real, k::Real=ustrip(u"u * nm^2 * ps^-2 * K^-1", Unitful.k);
                dims=3, rng=Random.default_rng())
```

Generate a random velocity from the Maxwell-Boltzmann distribution, with optional custom Boltzmann constant.
