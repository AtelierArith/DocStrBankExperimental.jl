```
Codata
```

Object to hold the natural constants from CODATA. It is best created with the function [`castCodata`](@ref)

The fields are:

  * `.∆νCs`: Cs hyperfine transition frequency (`::Value`)
  * `.c`: speed of light in vacuum (`::Value`)
  * `.h`: Planck constant (`::Value`)
  * `.ħ`: Planck constant - reduced (`::Value`)
  * `.e`: elementary charge (`::Value`)
  * `.kB`: Boltzmann constant (`::Value`)
  * `.NA`: Avogadro constant (`::Value`)
  * `.Kcd`: Luminous efficacy (`::Value`)
  * `.me`: electron rest mass (`::Value`)
  * `.R∞`: Rydberg constant (`::Value`)
  * `.Ry`: Rydberg frequency (`::Value`)
  * `.Eh`: Hartree a.u. (`::Value`)
  * `.α`: fine-structure constant (`::Value`)
  * `.μ0`: magnetic permitivity of vacuum (`::Value`)
  * `.ε0`: electric permitivity of vacuum (`::Value`)
  * `.KJ`: Josephson constant (`::Value`)
  * `.RK`: Von Klitzing constant (`::Value`)
  * `.R`: Molar gas constant (`::Value`)
  * `.u`: unified atomic mass unit (`::Value`)
  * `.matE`: unit conversion matrix (Matrix{Float64})

#### Example:

```
julia> codata = castCodata(2022);

julia> codata.μ0
Value(1.2566370612696005e-6, "N A⁻²")

julia> codata.μ0.val
1.2566370612696005e-6
```
