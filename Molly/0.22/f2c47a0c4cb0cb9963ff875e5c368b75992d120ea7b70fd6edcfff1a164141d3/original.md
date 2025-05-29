```
maxwell_boltzmann(atom_mass::Unitful.Mass, temp::Unitful.Temperature,
                  k::BoltzmannConstUnits=Unitful.k; rng=Random.default_rng())
maxwell_boltzmann(atom_mass::MolarMass, temp::Unitful.Temperature,
                  k_molar::MolarBoltzmannConstUnits=(Unitful.k * Unitful.Na);
                  rng=Random.default_rng())
maxwell_boltzmann(atom_mass::Real, temperature::Real,
                  k::Real=ustrip(u"u * nm^2 * ps^-2 * K^-1", Unitful.k);
                  rng=Random.default_rng())
```

Generate a random velocity along one dimension from the Maxwell-Boltzmann distribution, with optional custom Boltzmann constant.
