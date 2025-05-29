```
struct StrongAdmissibilityStd
```

Two blocks are admissible under this condition if the minimum of their `diameter` is smaller than `eta` times the `distance` between them, where `eta::Float64` is a parameter.

## Usage:

```julia
adm = StrongAdmissibilityStd(;eta=2.0)
adm(Xnode,Ynode)
```
