```
quarnetGoFtest!(net::HybridNetwork, df::DataFrame, optbl::Bool; quartetstat=:LRT, correction=:simulation, seed=1234, nsim=1000, verbose=false, keepfiles=false)
quarnetGoFtest!(net::HybridNetwork, dcf::DataCF,   optbl::Bool; kwargs...)
```

Goodness-of-fit test for the adequacy of the multispecies network coalescent, to see if a given population or species network explains the quartet concordance factor data adequately. The network needs to be of level 1 at most (trees fullfil this condition), and have branch lengths in coalescent units. The test assumes a multinomial distribution for the observed quartet concordance factors (CF), such that information on the number of genes for each four-taxon set (`ngenes` field) must be present.

For each four-taxon set, an outlier p-value is obtained by comparing a test statistic (-2log likelihood ratio by default) to a chi-square distribution with 2 degrees of freedom (see below for other options).

The four-taxon sets are then categorized as outliers or not, according to their outlier p-values (outlier if p<0.05). Finally, a one-sided goodness-of-fit test is performed on the frequency of outlier 4-taxon sets to see if there are more outliers than expected. The z-value for this test corresponds to the null hypothesis that 5% outlier p-values are < 0.05 (versus more than 5%):

$$
z = \frac{\mathrm{proportion.outliers} - 0.05}{\sqrt{0.05 \times 0.95/\mathrm{number.4taxon.sets}}}.
$$

This z-value corresponds to a test that assumes independent outlier p-values across 4-taxon sets: it makes no correction for dependence.

To correct for dependence with `correction=:simulation`, the distribution of z-values is obtained by simulating gene trees under the coalescent along the network (after branch length optimization if `optbl=true`) using [PhyloCoalSimulations](https://github.com/cecileane/PhyloCoalSimulations.jl). The z-score is calculated on each simulated data set. Under independence, these z-scores have mean 0 and variance 1. Under dependence, these z-scores still have mean 0, but an inflated variance. This variance σ² is estimated from the simulations, and the corrected p-value is obtained by comparing the original z value to N(0,σ²). When `correction=:none`, σ is taken to be 1 (independence): *not* recommended!

  * The first version takes a `DataFrame` where each row corresponds to a given four-taxon set. The data frame is modified by having an additional another column containing the p-values corresponding to each four-taxon set.
  * The second version takes a `DataCF` object and modifies it by updating the expected concordance factors stored in that object.

Note that `net` is **not** modified.

# arguments

  * `optbl`: when `false`, branch lengths in `net` are taken as is, and need to be in coalescent units. When `optbl=true`, branch lengths in `net` are optimized, to optimize the pseudo log likelihood score as in SNaQ (see [here](https://crsl4.github.io/PhyloNetworks.jl/stable/lib/public/#PhyloNetworks.topologyMaxQPseudolik!)). In both cases, any missing branch length is assigned a value with [`ultrametrize!`](@ref), which attempts to make the major tree ultrametric (but never modifies an existing edge length). Missing branch lengths may arise if they are not identifiable, such as lengths of external branches if there is a single allele per taxon. The network is returned as part of the output.

# keyword arguments

  * `quartetstat`: the test statistic used to obtain an outlier p-value for each four-taxon set, which is then compared to a chi-squared distribution with 2 degrees of freedom to get a p-value.

      * `:LRT` is the default, for the likelihood ratio: $2n_\mathrm{genes} \sum_{j=1}^3 {\hat p}_j (\log{\hat p}_j - \log p_j)$ where $p_j$ is the quartet CF expected from the network, and ${\hat p}_j$ is the quartet CF observed in the data.
      * `:Qlog` for the Qlog statistics (Lorenzen, 1995): $2n_\mathrm{genes} \sum_{j=1}^3 \frac{({\hat p}_j - p_j)^2}{p_j (\log{\hat p}_j - \log p_j)}$ and
      * `:pearson` for Pearon's chi-squared statistic, which behaves poorly when one or more expected counts are low (e.g. less than 5): $n_\mathrm{genes} \sum_{j=1}^3 \frac{({\hat p}_j - p_j)^2 }{p_j}$
  * `correction=:simulation` to correct for dependence across 4-taxon. Use `:none` to turn off simulations and the correction for dependence.
  * `seed=1234`: master seed to control the seeds for gene tree simulations.
  * `nsim=1000`: number of simulated data sets. Each data set is simulated to have the median number of genes that each 4-taxon sets has data for.
  * `verbose=false`: turn to `true` to see progress of simulations and to diagnose potential issues.
  * `keepfiles=false`: if true, simulated gene trees are written to files, one file for each of the 1000 simulations. If created (with `keepfiles=true`), these files are stored in a newly created folder whose name starts with `jl_` and is placed in the current directory.

# output

1. p-value of the overall goodness-of-fit test (corrected for dependence if requested)
2. uncorrected z value test statistic
3. estimated σ for the test statistic used for the correction (1.0 if no correction)
4. a vector of outlier p-values, one for each four-taxon set
5. network (first and second versions): `net` with loglik field updated if `optbl` is false;  copy of `net` with optimized branch lengths and loglik if `optbl` is true
6. in case `correction = :simulation`, vector of simulated z values (`nothing` if `correction = :none`). These z-values could be used to calculate an empirical p-value (instead of the p-value in #1), as the proportion of simulated z-values that are ⩾ the observed z-value (in #2).

# references

  * Ruoyi Cai & Cécile Ané (2021). Assessing the fit of the multi-species network coalescent to multi-locus data. Bioinformatics, 37(5):634-641. doi: [10.1093/bioinformatics/btaa863](https://doi.org/10.1093/bioinformatics/btaa863)
  * Lorenzen (1995). A new family of goodness-of-fit statistics for discrete multivariate data. Statistics & Probability Letters, 25(4):301-307. doi: [10.1016/0167-7152(94)00234-8](https://doi.org/10.1016/0167-7152(94)00234-8)
