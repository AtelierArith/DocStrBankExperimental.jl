```
BasisSet
```

Object holding a set of BasisFunction objects associated with an array of atoms.

# Fields

| Name       | Type                            | Description                                                                     |
|:---------- |:------------------------------- |:------------------------------------------------------------------------------- |
| `atoms`    | `Vector{Atom}`                  | An array of `Molecules.Atom` objects                                            |
| `name`     | `String`                        | String holding the basis set name                                               |
| `basis`    | `Vector{Vector{BasisFunction}}` | An Array of arrays with BasisFunction                                           |
| `natoms`   | `Int32`                         | Number of atoms in the BasisSet                                                 |
| `nbas`     | `Int32`                         | Number of basis functions (Note, not equal the number of BasisFunction objects) |
| `nshells`  | `Int32`                         | Number of shells, i.e. BasisFunction objects                                    |
| `lc_atoms` | `Array{Int32,1}`                | Integer array maping data to libcint                                            |
| `lc_bas`   | `Array{Int32,1}`                | Integer array maping data to libcint                                            |
| `lc_env`   | `Array{Float64,1}`              | Float64 array maping data to libcint                                            |

# Example

Build a basis set from default options

```julia
julia> water = Molecules.parse_string(
"O        1.2091536548      1.7664118189     -0.0171613972
 H        2.1984800075      1.7977100627      0.0121161719
 H        0.9197881882      2.4580185570      0.6297938832"
)
julia> bset = BasisSet("sto-3g", water)
sto-3g Basis Set
Number of shells: 5
Number of basis:  7

O: 1s 2s 1p 
H: 1s 
H: 1s
```

The BasisSet object can be accessed as two-dimensional array.

```julia
julia> bset[1,2] # Show the second basis for the first atom (O 2s)
S shell with 1 basis built from 3 primitive gaussians

χ₀₀  =    0.8486970052⋅Y₀₀⋅exp(-5.033151319⋅r²)
     +    1.1352008076⋅Y₀₀⋅exp(-1.169596125⋅r²)
     +    0.8567529838⋅Y₀₀⋅exp(-0.38038896⋅r²)
```

You can also create your own crazy mix! Lets create one S and one P basis functions for H

```julia
julia> h2 = Molecules.parse_string(
   "H 0.0 0.0 0.0
    H 0.0 0.0 0.7"
)
julia> s = BasisFunction(0, [0.5215367271], [0.122])
julia> p = BasisFunction(1, [1.9584045349], [0.727])
```

The basis set is constructed with an array of atoms (Vector{Atom}) and a corresponding array of Vector{BasisFunction} holding all basis functions for that particular atom. In this example, we consider an unequal treatment for the two atoms in the H₂ molecule.

```
julia> shells = [
    [s],  # A s function on the first hydrogen
    [s,p] # One s and one p function on the second hydrogen
]
julia> BasisSet("UnequalHydrogens", h2, shells)
UnequalHydrogens Basis Set
Number of shells: 3
Number of basis:  5

H: 1s 
H: 1s 1p
```
