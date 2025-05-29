The `buildbasis` method takes a `Molecule` as input and return for us an array of `GaussianBasis` types. For example, let's open the same  `h2.xyz` example. As a standard basis set, we use STO-3G data.

```julia
2 

H      -1.788131055      0.000000000     -4.028513155
H      -1.331928651      0.434077746     -3.639854078
```

We give the file as an input:

```julia
hydrogen = molecule("h2.xyz")
sto3g = buildbasis(hydrogen)
```
