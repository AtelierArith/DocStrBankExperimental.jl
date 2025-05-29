```
loadjets!(filename, jets; splitby=isspace, constructor=(px,py,pz,E)->LorentzVectorHEP(E,px,py,pz), dtype=Float64)
```

Loads the `jets` from a file. Ignores lines that start with `'#'`. Each line gets processed in the following way: the line is split using `split(line, splitby)` or simply `split(line)` by default. Every value in this line is then converted to the `dtype` (which is `Float64` by default). These values are then used as arguments for the `constructor` function which should produce individual jets. By default, the `constructor` constructs Lorentz vectors.

Everything that was already in `jets` is not affected as we only use `push!` on it.

# Example

```julia
# Load jets from two files into one array
jets = []
loadjets!("myjets1.dat", jets)
loadjets!("myjets2.dat", jets)
```
