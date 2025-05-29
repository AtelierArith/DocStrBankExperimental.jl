```julia
abstract type RelaxTag
```

An `abstract type` the subtypes of which define the manner of relaxation that will be performed for each operator applied to the MC object. Currently, the `struct NS` which specifies that standard (Mitsos 2009) are to be used is fully supported. Limited support is provided for differentiable McCormick relaxations specified by `struct Diff` (Khan 2017) and struct MV `struct MV` (Tsoukalas 2011.) A rounding-safe implementation of the standard McCormick relaxations is specified by the struct `NSSafe` which is work in progress.
