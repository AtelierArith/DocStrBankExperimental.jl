```
listCodata(codata::Codata)
```

Method to list the fields of [`Codata`](@ref) by their symbolic name

#### Example:

```
julia> julia> codata = castCodata(2018);

julia> listCodata(codata)
∆νCs = 9192631770 Hz      - ¹³³Cs hyperfine transition frequency
   c = 299792458 m s⁻¹    - speed of light in vacuum
   h = 6.62607e-34 J Hz⁻¹ - Planck constant
   ħ = 1.05457e-34 J s    - Planck constant (reduced)
   e = 1.60218e-19 C      - elementary charge
  kB = 1.38065e-23 J K⁻¹  - Boltzmann constant
  NA = 6.02214e23 mol⁻¹   - Avogadro constant
 Kcd = 683 lm W⁻¹         - Luminous efficacy
  mₑ = 9.10938e-31 kg     - electron mass
  mₚ = 1.67262e-27 kg     - proton mass
  R∞ = 1.09737e7 m⁻¹      - Rydberg constant
  Ry = 3.28984e15 Hz      - Rydberg frequency
  Eₕ = 4.35974e-18 J      - Hartree atomic unit
   α = 0.00729735         - fine-structure constant
  a0 = 5.29177e-11 m      - Bohr radius
  μB = 9.27401e-24 J T⁻¹  - Bohr magneton
  μN = 5.05078e-27 J T⁻¹  - nuclear magneton
  μ₀ = 1.25664e-6 N A⁻²   - magnetic permitivity of vacuum
  ε₀ = 8.85419e-12 F m⁻¹  - electric permitivity of vacuum
  KJ = 4.83598e14 Hz V⁻¹  - Josephson constant
  RK = 25812.8 Ω          - Von Klitzing constant
   R = 8.31446 J mol⁻¹K⁻¹ - Molar gas constant
   u = 1.66054e-27 kg     - unified atomic mass unit
```
