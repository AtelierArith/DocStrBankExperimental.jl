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

一次元に沿ったランダムな速度をマクスウェル-ボルツマン分布から生成し、オプションでカスタムボルツマン定数を指定します。
