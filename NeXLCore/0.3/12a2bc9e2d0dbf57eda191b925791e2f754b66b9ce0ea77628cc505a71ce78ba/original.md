```
z(mat::Material) = z(Donovan2002, mat)
z(::Type{NaiveZ|ElectronFraction|AtomicFraction}, mat::Material)
z(::Type{ElasticFraction}, mat::Material, e::AbstractFloat)
z(::Type{Donovan2002}, mat::Material; exponent=0.667)
```

Compute the mean atomic number for a material.

```
Algorithms:
  * NaiveZ - Mass fraction averaging
  * AtomFraction - Atom fraction averaging
  * ElectronFraction - Simple electron fraction averaging
  * ElasticFraction - Scattering cross-section averaged
  * Donovan2002 - Yukawa/Donovan modified exponent electron fraction averaging
```

For more details see Mean Z algorithm in J.J. Donovan, N.E. Pingitore, Microsc. Microanal. 2002 ; 8 , 429 (also see Microsc. Microanal. 27 (Suppl 1), 2021))
