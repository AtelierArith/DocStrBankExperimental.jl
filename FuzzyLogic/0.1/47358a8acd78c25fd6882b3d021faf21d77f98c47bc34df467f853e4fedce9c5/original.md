```julia
readfis(file::String) -> FuzzyLogic.AbstractFuzzySystem
readfis(
    file::String,
    fmt::Union{Nothing, Symbol}
) -> FuzzyLogic.AbstractFuzzySystem

```

Read a fuzzy system from a file using a specified format.

### Inputs

  * `file::String` – path to the file to read.
  * `fmt::Union{Symbol,Nothing}` – input format of the file. If `nothing`, it is inferred from the file extension.

Supported formats are

  * `:fcl` – Fuzzy Control Language (corresponding file extension `.fcl`)
  * `:fml` – Fuzzy Markup Language (corresponding file extension `.xml`)
  * `:matlab` – Matlab fis (corresponding file extension `.fis`)
