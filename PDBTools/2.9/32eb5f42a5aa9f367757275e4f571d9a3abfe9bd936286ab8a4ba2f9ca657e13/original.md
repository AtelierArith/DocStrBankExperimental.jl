```
distance(x,y)
```

Computes the minimum distance between two sets of atoms, between an atom and a set of atoms, or simply  the distance between two atoms, or from the coordinates or sets of coordinates. 

The input may be an `Atom` vector of `Atom`s, or a 3D vector, or a vector of 3D vector of coordinates, for examples as output by the `coor` function.

### Examples

```julia-repl
julia> model = wget("1BSX");

julia> protein = select(model,"protein");

julia> ligand = select(model,"resname T3");

julia> distance(protein,ligand)
2.7775834820937417

julia> distance(protein[1],ligand[3])
36.453551075306784

julia> distance(coor(ligand),protein)
2.7775834820937417

```
