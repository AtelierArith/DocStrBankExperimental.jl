```
PopData
    metadata::PopDataInfo
    genodata::DataFrame
```

The data struct used for the PopGen population genetics ecosystem. You are **strongly** discouraged from manually creating tables to pass into a PopData, and instead should use the provided file importers and utilities.

```
- `metadata` PopDataInfo of  data information
    - `samples` - the number of samples in the data
    - `sampleinfo` - DataFrame of sample names,populations, ploidy, etc.
    - `loci` - the number of loci in the data
    - `locusinfo` - DataFrame of locus names, chromosome, physical position, etc.
    - `populations` - the number of populations in the data
    - `ploidy` - the ploidy (or ploidies) present in the data
    - `biallelic` - if all the markers are biallelic
- `genodata` DataFrame of sample genotype records
    - `name` - the individual/sample names [`PooledArray`]
    - `population` - population names [`PooledArray`]
    - `locus` - locus names [`PooledArray`]
    - `genotype` - genotype values [`NTuple{N,Signed}`]
```
