```
generateclassdata(c[, shuffle])
```

Generates 3 classes of data given a `ClassData` struct as an input. Returns a matrix  containing the 3 classes of signals and a vector containing their corresponding labels.

Based on N. Saito and R. Coifman in "Local Discriminant Basis and their Applications" in the Journal of Mathematical Imaging and Vision, Vol. 5, 337-358 (1995).

# Arguments

  * `c::ClassData`: Type of signal classes to generate.
  * `shuffle::Bool`: (Default: `true`). Whether or not to shuffle the signals.

# Returns

  * `::Matrix{Float64}`: Generated signals.
  * `::Vector{Int64}`: Class corresponding to each column of generated signals.

# Examples

```@repl
using WaveletsExt

c = ClassData(:tri, 100, 100, 100)
generateclassdata(c)
```

**See also:** [`ClassData`](@ref)
