```
hwetest(data::PopData; by::String = "locus", correction = "none")
```

Calculate chi-squared test of HWE for each locus and returns observed and expected heterozygosity with chi-squared, degrees of freedom and p-values for each locus. Use `by = "population"` to perform this separately for each population (default: `by = "locus"`). Use `correction =` to specify a P-value adjustment method for multiple testing.

#### example

`hwetest(@gulfsharks, correction = "bh")` 

`hwetest(@gulfsharks, by = "population", correction = "bh")` 

### `correction` methods (case insensitive)

  * `"bonferroni"` : Bonferroni adjustment
  * `"holm"` : Holm adjustment
  * `"hochberg"` : Hochberg adjustment
  * `"bh"` : Benjamini-Hochberg adjustment
  * `"by"` : Benjamini-Yekutieli adjustment
  * `"bl"`  : Benjamini-Liu adjustment
  * `"hommel"` : Hommel adjustment
  * `"sidak"` : Šidák adjustment
  * `"forwardstop"` or `"fs"` : Forward-Stop adjustment
  * `"bc"` : Barber-Candès adjustment
