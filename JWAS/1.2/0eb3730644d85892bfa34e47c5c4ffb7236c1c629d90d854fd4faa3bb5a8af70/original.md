```
get_genotypes(file::Union{AbstractString,Array{Float64,2},Array{Float32,2},Array{Any,2},DataFrames.DataFrame},G=false;
              separator=',',header=true,rowID=false,
              center=true,quality_control=false,
              method = "RR-BLUP",Pi = 0.0,estimatePi = true,estimateScale=false,
              G_is_marker_variance = false,df = 4.0)
```

  * Get marker informtion from a genotype file/matrix. This file needs to be column-wise sorted by marker positions.

      * If a text file is provided, the file format should be:

        ```
        Animal,marker1,marker2,marker3,marker4,marker5
        S1,1,0,1,1,1
        D1,2,0,2,2,1
        O1,1,2,0,1,0
        O3,0,0,2,1,1
        ```
      * If an nxp Matrix of genotypes (Array or DataFrame) is provided, where n is the number of individuals and p is the number of markers,

          * This matrix needs to be column-wise sorted by marker positions.
          * rowID is a vector of individual IDs, e.g.,rowID=["a1","b2","c1"]; if it is omitted, IDs will be set to 1:n
          * header is a header vector such as ["id"; "mrk1"; "mrk2";...;"mrkp"]. If omitted, marker names will be set to 1:p
  * If `quality_control`=true, defaulting to `true`,

      * Missing genotypes should be denoted as `9`, and will be replaced by column means. Users can also impute missing genotypes before the analysis.
      * Minor allele frequency `MAF` threshold, defaulting to `0.01`, is uesd, and fixed loci are removed.
  * **G** is the mean for the prior assigned for the genomic variance with degree of freedom **df**, defaulting to 4.0. If **G** is not provided, a value is calculated from responses (phenotypes).
  * Available `methods` include "conventional (no markers)", "RR-BLUP", "BayesA", "BayesB", "BayesC", "Bayesian Lasso", and "GBLUP".
  * In Bayesian variable selection methods, `Pi` for single-trait analyses is a number; `Pi` for multi-trait analyses is a dictionary such as `Pi=Dict([1.0; 1.0]=>0.7,[1.0; 0.0]=>0.1,[0.0; 1.0]=>0.1,[0.0; 0.0]=>0.1)`, defaulting to `all markers have effects (Pi = 0.0)` in single-trait analysis and `all markers have effects on all traits (Pi=Dict([1.0; 1.0]=>1.0,[0.0; 0.0]=>0.0))` in multi-trait analysis. `Pi` is estimated if `estimatePi` = true, , defaulting to `false`.
  * Scale parameter for prior of marker effect variance is estimated if `estimateScale` = true, defaulting to `false`.
