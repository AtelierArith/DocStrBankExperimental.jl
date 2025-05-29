```
genepop(infile::String; kwargs...)
```

Load a Genepop format file into memory as a PopData object.

  * `infile::String` : path to Genepop file

### Keyword Arguments

  * `digits::Integer`: number of digits denoting each allele (default: `3`)
  * `popsep::String` : word that separates populations in `infile` (default: "POP")
  * `silent::Bool`   : whether to print file information during import (default: `false`)
  * `allow_monomorphic::Bool` : whether to keep monomorphic loci in the dataset (default: `false`)

### File must follow standard Genepop formatting:

  * First line is a comment (and skipped)
  * Loci are listed after first line as one-per-line without commas or in single comma-separated row
  * A line with a particular keyword (default `POP`) must delimit populations
  * Sample name is immediately followed by a *comma*
  * File is *tab or space delimted* (but not both!)

### Genepop file example:

```
wasp_hive.gen: Wasp populations in New York
Locus1
Locus2
Locus3
pop
Oneida_01,  250230  564568  110100
Oneida_02,  252238  568558  100120
Oneida_03,  254230  564558  090100
pop
Newcomb_01, 254230  564558  080100
Newcomb_02, 000230  564558  090080
Newcomb_03, 254230  000000  090100
Newcomb_04, 254230  564000  090120
```

## Example

```
waspsNY = genepop("wasp_hive.gen", digits = 3, popsep = "pop")
```
