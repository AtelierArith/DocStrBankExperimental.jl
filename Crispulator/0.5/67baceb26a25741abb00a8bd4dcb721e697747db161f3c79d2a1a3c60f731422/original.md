```julia
differences_between_bins(raw_data)

```

Given the raw data from [`Crispulator.sequencing`](@ref) returns two DataFrames

1. `guide_data`: This DataFrame contains the per-guide level data including the  log2 fold change in the normalized frequencies of each guide between each  pairwise combination of bins. Thus, if there are `n` bins, then it computes  the log2 fold changes for the $\frac{n!}{2(n-2)!}$ combinations
2. `gene_data`: This DataFrame contains the same information but grouped by  gene. The log2 fold change data from the first DataFrame is used to calculate  the average log2 fold change per gene and a pvalue computed using a  [Mann-Whitney U-test](https://en.wikipedia.org/wiki/Mann-Whitney_U_test) as  measure of how consistently shifted the guides are of this gene versus the  population of negative control guides. (see below for more info)

A typical 2 bin `guide_data` DataFrame contains the following columns:

| Column Name            | Meaning                                                                                                                                                                                                                                   |
|:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `gene`                 | the gene ID of that this guide targets                                                                                                                                                                                                    |
| `knockdown`            | activity of the guide on 0 to 1 scale, where 1 is complete knockout                                                                                                                                                                       |
| `barcodeid`            | the ID of this specific guide                                                                                                                                                                                                             |
| `theo_phenotype`       | expected phenotype of this guide, generally a -1 to 1 scale                                                                                                                                                                               |
| `behavior`             | whether the target gene displays a linear or sigmoidal response to incomplete knockdown (see [`Crispulator.Library`](@ref) for more details)                                                                                              |
| `class`                | which phenotype distribution the target gene was drawn from (see [`Crispulator.Library`](@ref) for more details). Serves as the "ground truth" label against which screen performance is evaluated, e.g. with [`Crispulator.auprc`](@ref) |
| `initial_freq`         | frequency of guide post-transfection (see [`Crispulator.transfect`](@ref))                                                                                                                                                                |
| `counts_bin1`          | the raw number of reads for each guide in the first bin                                                                                                                                                                                   |
| `freqs_bin1`           | the number of reads for each guide divided by the total number of reads in this bin                                                                                                                                                       |
| `rel_freqs_bin1`       | the frequency of each guide divided by the median frequency of negative control guides                                                                                                                                                    |
| `counts_bin2`          | the raw number of reads for each guide in the second bin                                                                                                                                                                                  |
| `freqs_bin2`           | the number of reads for each guide divided by the total number of reads in this bin                                                                                                                                                       |
| `rel_freqs_bin2`       | the frequency of each guide divided by the median frequency of negative control guides for this bin                                                                                                                                       |
| `log2fc_bin2_div_bin1` | the log2 fold change in relative guide frequencies between `bin2` and `bin1`, equivalent to `log2(rel_freqs_bin2/rel_freqs_bin1)`                                                                                                         |

A typical `gene_data` DataFrame contains the following data:

| Column Name                  | Meaning                                                                                                                                                                                                                         |
|:---------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `gene`                       | this gene's ID                                                                                                                                                                                                                  |
| `class`                      | see above                                                                                                                                                                                                                       |
| `behavior`                   | see above                                                                                                                                                                                                                       |
| `mean_bin2_div_bin1`         | the mean log 2 fold change in relative frequencies between from `bin1` to `bin2` for all the guides targeting this gene. Calculated as $\frac{1}{k}\sum_k \text{log2fc_bin2_div_bin1}_k$ for the $k$ guides targeting each gene |
| `pvalue_bin2_div_bin1`       | the -log10 pvalue of the log2 fold changes of all guides targeting this gene as computed by the non-parametric Mann-Whitney U-test. A measure of the consistency of the log 2 fold changes[^1]                                  |
| `absmean_bin2_div_bin1`      | absolute value of `mean_bin2_div_bin1` per-gene                                                                                                                                                                                 |
| `pvalmeanprod_bin2_div_bin1` | `mean_bin2_div_bin1` multiplied with the `pvalue_bin2_div_bin1` per-gene                                                                                                                                                        |

# Further reading

[^1]: Kampmann M, Bassik MC, Weissman JS. Integrated platform for genome-wide screening and construction of high-density genetic interaction maps in mammalian cells. *Proc Natl Acad Sci U S A*. 2013;110:E2317–26.
