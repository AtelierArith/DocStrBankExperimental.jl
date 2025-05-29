```
ticr!(net::HybridNetwork, df::DataFrame, optbl::Bool; quartetstat, test)
ticr!(net::HybridNetwork, dcf::DataCF,   optbl::Bool; quartetstat, test)
ticr(dcf::DataCF, quartetstat::Symbol, test::Symbol)
```

Goodness-of-fit test for the adequacy of the multispecies network coalescent, to see if a given population or species network explains the quartet concordance factor data adequately. See Stenz et al 2015 and [addendum](http://www.stat.wisc.edu/~ane/publis/2015Stenz_TICR_addendum.pdf) for the method on trees, from which the acronym TICR was derived: Tree Incongruence Checking with R.

The tree / network needs to have branch lengths in coalescent units, and must be of level 1. It must be fully resolved, such that the "major" quartet is clearly defined, even though branch lengths can be 0.

The Dirichlet distribution is used to fit the distribution of the observed quartet concordance factors (CF), with a concentration parameter estimated from the data.

The four-taxon sets are then binned into categories according to their outlier p-values: `0-0.01`, `0.01-0.05`, `0.05-0.10`, and `0.10-1`. Finally, a one-sided goodness-of-fit test is performed on these binned frequencies to determine if they depart from an expected 5% p-values being below 0.05 (versus more than 5%), using the default `test = :onesided`. Alternatively, the option `test = :goodness` carries out the overall goodness-of-fit chi-square test proposed by Stenz et al. (2015), to test for any kind of departure from the expected frequencies (0.01, 0.04, 0.05, 0.90) across all 4 bins.

  * The first version takes a `DataFrame` where each row corresponds to a given four-taxon set. The data frame is modified by having an additional another column containing the outlier p-values corresponding to each four-taxon set.
  * The second version takes a `DataCF` object and modifies it by updating the expected concordance factors stored in that object.
  * The last version (which all others call) assumes that the expected concordance factors in the `DataCF` object are correctly calculated from the test network.

# arguments

  * `optbl`: when `false`, the loglik field of `net` is updated but branch lengths are taken as is. When `true`, a copy of `net` is used to conduce the test, with updated branch lengths (in coalescent units) and updated loglik. This network is returned.
  * `quartetstat = :maxCF`: test statistic used to obtain an outlier p-value for each four-taxon set. By default, it is the absolute difference between the observed CF and expected CF of the major resolution (which has the largest CF) if `quartetstat=:maxCF`, as used in Stenz et al. (2015). The other option is `quartetstat=:minpval`, in which case the absolute difference between the observed CF and expected CF is calculated for all 3 resolutions, leading to 3 (non-independent) p-values. The outlier p-value for a given four-taxon set is taken as the minimum of these 3 p-values. This option can detect all kinds of departure from the network model for a given four-taxon set, but is not recommended because it is very liberal.
  * `test = :onesided`: the overall goodness-of-fit test performed on binned frequencies of quartet outlier p-values; see above.

# output

1. p-value of the overall goodness-of-fit test
2. test statistic (z value)
3. a dictionary of the count of p-values in each of the four category
4. a vector of two test parameters for the Dirichlet distribution:

      * value of the concentration parameter α
      * value of the pseudo likelihood (optimized at α)
5. a vector of outlier p-values, one for each four-taxon set
6. network (first and second versions): `net` with loglik field updated if `optbl` is false;  copy of `net` with optimized branch lengths and loglik if `optbl` is true

# references

NWM Stenz, B Larget, DA Baum and C Ané (2015). Exploring tree-like and non-tree-like patterns using genome sequences: An example using the inbreeding plant species *Arabidopsis thaliana* (L.) Heynh. Systematic Biology, 64(5):809-823. doi: [10.1093/sysbio/syv039](https://doi.org/10.1093/sysbio/syv039)

see also this [addendum](http://www.stat.wisc.edu/~ane/publis/2015Stenz_TICR_addendum.pdf)
