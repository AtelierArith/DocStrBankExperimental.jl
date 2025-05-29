```
bool = check_ped(pedlist [, parentsfirst, warning])
```

Checks if the pedigree list has no apparent error. The pedigree list `pedlist` is an integer matrix generated with `ReadPedigree` from a file. This function checks the following errors.

  * Sires (or dams) appear as dams (or sires).
  * The list has a loop i.e., an animal's ancestor is also progeny of the animal.
  * Parents precede their progeny i.e., IDs are chronologically sorted (optional; checked with `parentsfirst=true`).

It returns `true` with no error but `false` with a warning message where the error is (omit with `warining=false`).

### Examples

```jldoctest
julia> using PedigreeTools;

julia> pedlist,idtable = read_ped("pedigree.txt");

julia> check_ped(pedlist)
true

# checks if parents precede their progeny
julia> check_ped(pedlist, parentsfirst=true)
true
```
