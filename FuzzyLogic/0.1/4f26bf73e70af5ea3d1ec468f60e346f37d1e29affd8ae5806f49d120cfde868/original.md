```julia
compilefis(
    fname::AbstractString,
    fis::FuzzyLogic.AbstractFuzzySystem
) -> Any
compilefis(
    fname::AbstractString,
    fis::FuzzyLogic.AbstractFuzzySystem,
    name::Symbol
) -> Any

```

Compile the fuzzy inference system into stand-alone Julia code. If the first argument is a string, it write the code in the given file, otherwise it returns the Julia expression of the code.

### Inputs

  * `fname::AbstractString` – file where to write
  * `fis::AbstractFuzzySystem` – fuzzy system to compile
  * `name::Symbol` – name of the generated function, default `fis.name`

### Notes

Only type-1 inference systems are supported
