```
add_genotypes(mme::MME,M::Union{AbstractString,Array{Float64,2},Array{Float32,2},Array{Any,2},DataFrames.DataFrame},G=false;
              header=false,rowID=false,separator=',',
              center=true,G_is_marker_variance=false,df=4)
```

  * Get marker informtion from a genotype file or an nxp Matrix M of genotypes (Array or DataFrame), where n is the number of individuals and p is the number of markers. This file/matrix needs to be column-wise sorted by marker positions.
  * **G** is the mean for the prior assigned for the genomic variance with degree of freedom **df**, defaulting to 4.0. If **G** is not provided, a value is calculated from responses (phenotypes)
  * If a text file is provided, the file format should be:

      * ```
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
