```
function run_rqtl(dataset::String, trait::String; method::String="hk",
              model::String="normal", n_perm::Int64=0,
              control_marker::String="",
              gn_url::String=gn_url())
```

Runs R/qtl's `scanone` function with the specified `trait` in the specified `dataset`.

Some optional arguments have analogs in options in the parent `scanone` function.  See the [help for that function](https://rqtl.org/manual/qtl-manual.pdf).

Optional arguments inlcude:

  * method (default="hk"): possible values are

      * hk: Haley-Knott method
      * em: EM algorithm
      * ehk: Extended EM algorithm
      * imp: multiple imputation
      * mr: marker regression dropping individuals with missing genotypes
      * mr-imp: marker regression filling in missing data with a single imputation
      * mr-argmax: marker regression filling in by the Viterbi algorithm
  * model (default="normal"): model for trait given genotypes; possible values are

      * normal: equivalent to linear regression with complete data
      * binary: equivalent to logistic regression with complete data
      * 2part: two-part model for trait given genotype
      * np: non-parametric analysis
  * n_perm (default=0) number of permutations to perform
  * control_marker: name of marker to control for as an additive covariate
