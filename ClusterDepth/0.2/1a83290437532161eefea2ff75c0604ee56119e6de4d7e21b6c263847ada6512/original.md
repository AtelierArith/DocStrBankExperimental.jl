using Base: Stateful clusterdepth(rng,data::AbstractArray;τ=2.3, statfun=x->abs.(studentt(x)),permfun=sign*permute!,nperm=5000,pval*type=:troendle)

calculate clusterdepth of given datamatrix. 

  * `data`: `statfun` will be applied on last dimension of data (typically this will be subjects)

Optional

  * `τ`: Cluster-forming threshold
  * `nperm`: number of permutations, default 5000
  * `stat_type`: default  the one-sample `t-test`, custom function can be specified (see `statfun!` and `statfun`)
  * `side_type`: default: `:abs` - what function should be applied after the `statfun`? could be `:abs`, `:square`, `:positive` to test positive clusters, `:negative` to test negative clusters. Custom function can be provided, see `sidefun``
  * `perm_type`: default `:sign` for one-sample data (e.g. differences), performs sign flips. custom function can be provided, see  `permfun`
  * `pval_type`: how to calculate pvalues within each cluster, default `:troendle`, see `?pvals`
  * `statfun` / `statfun!` a function that either takes one or two arguments and aggregates over last dimension. in the two argument case we expect the first argument to be modified inplace and provide a suitable Vector/Matrix.
  * `sidefun`: default `abs`. Provide a function to be applied on each element of the output of  `statfun`.
  * `permfun` function to permute the data, should accept an RNG-object and the data. can be inplace, the data is copied, but the same array is shared between permutations
