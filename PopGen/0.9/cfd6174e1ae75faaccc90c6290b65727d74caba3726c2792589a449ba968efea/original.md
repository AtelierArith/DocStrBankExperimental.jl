```
kinshiptotable(kinshipresults::T, methd::Symbol) where T<:NamedMatrix
```

Converts the `NamedMatrix` result from the non-bootstrapped `kinship()` results into a `DataFrame`. The second positonal argument (`methd`) is the name of the value column (default: `kinship`). For better analysis workflow, it would be useful to specify the method for this column, to keep track of which estimator was used (e.g., `Blouin`, `LynchLi`, etc.)

**Example**

```julia
julia> cats = @nancycats ; kin = kinship(cats, method = Moran) ;

julia> kinshiptotable(kin, :Moran)
22366×3 DataFrame
   Row │ sample1  sample2  Moran      
       │ String   String   Float64      
───────┼────────────────────────────────
     1 │ cc_001   cc_002    0.00688008
     2 │ cc_001   cc_003   -0.0286812
     3 │ cc_001   cc_005   -0.000749142
     4 │ cc_001   cc_007    0.0516361
     5 │ cc_001   cc_008    0.0261128
     6 │ cc_001   cc_009   -0.00187027
     7 │ cc_001   cc_010    0.0182852
   ⋮   │    ⋮        ⋮          ⋮
 22361 │ seg_028  seg_029  -0.0472928
 22362 │ seg_028  seg_030  -0.0172853
 22363 │ seg_028  seg_031  -0.00240921
 22364 │ seg_029  seg_030  -0.0278483
 22365 │ seg_029  seg_031   0.0297876
 22366 │ seg_030  seg_031  -0.0371295
                      22353 rows omitted
```
