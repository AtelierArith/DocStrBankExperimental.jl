```
SymplecticPositionVerlet()
```

密度を[`ContinuityDensity`](@ref)で統合する際の弱圧縮SPH（WCSPH）用に修正されたリープフロッグ積分スキーム。このスキームはSPHコード[DualSPHysics](https://github.com/DualSPHysics/DualSPHysics)によって使用されています。詳細は[https://github.com/DualSPHysics/DualSPHysics/wiki/3.-SPH-formulation#372-symplectic-position-verlet-scheme](https://github.com/DualSPHysics/DualSPHysics/wiki/3.-SPH-formulation#372-symplectic-position-verlet-scheme)および[Domínguez et al. 2022, Section 2.5.2](@cite Dominguez2022)を参照してください。

詳細については[time integration](@ref time_integration)を参照してください。
