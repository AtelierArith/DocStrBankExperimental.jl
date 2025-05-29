```
ランダム速度(atom_mass::Union{Unitful.Mass, MolarMass}, temp::Unitful.Temperature;
                dims=3, rng=Random.default_rng())
ランダム速度(atom_mass::Union{Unitful.Mass, MolarMass}, temp::Unitful.Temperature,
                k::Union{BoltzmannConstUnits, MolarBoltzmannConstUnits};
                dims=3, rng=Random.default_rng())
ランダム速度(atom_mass::Real, temp::Real, k::Real=ustrip(u"u * nm^2 * ps^-2 * K^-1", Unitful.k);
                dims=3, rng=Random.default_rng())
```

マクスウェル-ボルツマン分布からランダムな速度を生成します。オプションでカスタムボルツマン定数を指定できます。
