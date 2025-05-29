```
prandtl(T::Real,G::AbstractMole) = viscosity(T,G)*heatpressure(T,G)/thermalconductivity(T,G)
```

プラントル数は、運動量拡散率と熱拡散率の比（無次元）です。
