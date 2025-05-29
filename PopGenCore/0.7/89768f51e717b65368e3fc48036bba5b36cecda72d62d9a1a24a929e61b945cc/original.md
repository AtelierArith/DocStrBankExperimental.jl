```
plink(infile::String; keepfields::Symbol|Vector{Symbol}, silent::Bool)
```

Read a PLINK `.ped` or binary `.bed` file into memory as a `PopData` object. Requires an accompanying `.fam` file in the same directory, but an accompanying `.bim` file is optional.

  * `infile::String` : path to `.ped` or `.bed` file

### Keyword Arguments

  * `famfields::Symbol|Vector{Symbol}` : which additional fields to import from the `.fam` file

      * `:all` [default]
      * `:none`
      * any one or combination of `[:sire, :dam, :sex, :phenotype]`
  * `bimfields::Symbol|Vector{Symbol}` : which additional fields to import from the optional `.bim` file

      * `:all` [default]
      * `:none`
      * any one or combination of `[:chromosome, :cm, :bp]`
  * `silent::Bool`   : whether to print file information during import (default: `false`)

## Example

```julia
para = plink("datadir/parakeet.ped", famfields = :sex)
parr = plink("datadir/parrot.bed", famfields = [:sire, :dam], bimfields = :chromosome)
```
