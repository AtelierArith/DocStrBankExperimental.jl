```
f = get_inb(pedlist [,check, sorthere, method])
f = get_inb(s, d [,check, sorthere, method])
f = get_inb(Tv, pedlist [,check, sorthere, method])
```

Computes inbreeding coefficients for animals in a pedigree list `pedlist`. The list is an integer matrix (2 x *n*, where *n* is the number of animals). Or, you can provide the lists of sires and dams (`s` and `d`, respectively). The results are in the vector `f` with the type `Tv` (Float64 by default). Unknown parent groups (UPGs) will be replaced with a missing code (`0`).

The pedigree should be coded as parents precede their progeny. All descendent mush have a larger code than their ancestors. By default, the function checks if the pedigree is "permutaed", and stops if it is wrong. You can omit the check by `check=false`. If you want to permute the pedigree chronologically within this function, put `sorthere=true`.

The default method is Meuwissen and Luo (1992). This is the only method to be supported in this version.

### Examples

```jldoctest
julia> using PedigreeTools;

julia> pedlist,idtable = read_ped("pedigree.txt");

# assuming animals are chronologically sorted.
julia> f = get_inb(pedlist);

# sort animals here.
julia> f = get_inb(pedlist, sorthere=true);
```
