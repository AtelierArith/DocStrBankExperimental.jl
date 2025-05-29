```
pedlist,idtable = read_ped(filename [, integer, order, hasupg])
pedlist,idtable = read_ped(T, filename [, integer, order, hasupg])
```

Reads a pedigree file and store the pedigree list to an integer matrix `pedlist` (2 x *n*; where *n* is the number of animals found in the pedigree). The argument `T` defines the data type of `pedlist` and the default is Int. This function supports two types of ID: character and integer.

By default, this function reads the original as characters and converts it to an integer. The table is in a dictionary `idtable`, and it comes as the 2nd return-value. If the ID is an integer, you can put the option `integer=true`, where the function simply reads it as an integer without any conversion. No table is created so you will have a single return value, `pedlist`.

With integer coding, the function treats all sires and dams not in the animal field as real animals and creates new entries for them. It is not appropriate when your pedigree file is "renumbered" by RENUMF90 with unknown parent groups (UPGs) where UPG code is larger than the ID for real animals. The option `hasupg=true` does nothing for UPG in sire/dam fields so that such UPG-code stays in `pedlist` as is. The pedigree file has a space-separated text format with at least three fields: animal, sire, and dam ID. By default, the first three fields are assigned to these IDs.

The optional argument `order` changes the position of fields. The default is `order=[1,2,3]` and the 1st field for animal, the 2nd for sire, and the 3rd for dam.

### Examples

```jldoctest
julia> using PedigreeTools;

# for character data
julia> pedlist,idtable = read_ped("pedigree.txt");

# for character data with Int32 storage
julia> pedlist,idtable = read_ped(Int32,"pedigree.txt");

# for integer coding
julia> pedlist = read_ped("pedigree.txt", integer=true);
```
