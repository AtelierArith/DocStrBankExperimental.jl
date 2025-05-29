```
plink(data::PopData; filename::String)
```

Write a biallelic `PopData` object to PLINK `.ped` format with an accompanying `.fam` file. Genotypes are coded by the PLINK standard:

  * Integers are the alleles
  * `0` encodes missing
  * After column 6, every two numbers indicate a diploid genotype.

## Example

```julia
sharks = dropmultiallelic(@gulfsharks) ;
plink(sharks, filename = "biallelic_sharks.ped")
```
