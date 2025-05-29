```
mapallelesCFtable(mapping file, CF file; filename, columns, delim)
```

Create a new DataFrame containing the same concordance factors as in the input CF file, but with modified taxon names. Each allele name in the input CF table is replaced by the species name that the allele maps onto, based on the mapping file. The mapping file should have column names: allele and species.

Optional arguments:

  * `filename` to write/save resulting CF table. If not specified, then the output data frame is not saved to a file.
  * `columns` column numbers for the taxon names. 1-4 by default.
  * any keyword arguments that `CSV.File` would accept. For example, `delim=','` by default: columns are delimited by commas. Unless specified otherwise by the user, `pool=false` (to read taxon names as Strings, not levels of a categorical factor, for combining the 4 columns with taxon names more easily). The same CSV arguments are used to read both input file (mapping file and quartet file)

See also [`mapallelesCFtable!`](@ref) to input DataFrames instead of file names.

If a `filename` is specified, such as "quartetCF_speciesNames.csv" in the example below, this file is best read later with the option `pool=false`. example:

```julia
mapallelesCFtable("allele-species-map.csv", "allele-quartet-CF.csv";
                  filename = "quartetCF_speciesNames.csv")
df_sp = CSV.read("quartetCF_speciesNames.csv", DataFrame); # DataFrame object
dataCF_specieslevel = readtableCF!(df_sp, mergerows=true); # DataCF object
```
