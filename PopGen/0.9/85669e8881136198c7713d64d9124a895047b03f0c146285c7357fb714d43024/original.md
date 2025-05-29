```
genofreqtable(data::PopData; by::Union{Symbol,String} = "global")
```

Return a table of the observed `global` (default) or `population` genotype frequencies in a PopData object.

### Example:

```
julia> cats = @nancycats ;

julia> genofreqtable(cats)

341×4 DataFrame
 Row │ locus   genotype    count  frequency  
     │ String  Tuple…      Int64  Float64    
─────┼───────────────────────────────────────
   1 │ fca8    (135, 143)     16  0.0737327
   2 │ fca8    (133, 135)      9  0.0414747
   3 │ fca8    (135, 135)     23  0.105991
   4 │ fca8    (137, 143)      8  0.0368664
  ⋮  │   ⋮         ⋮         ⋮        ⋮
 338 │ fca37   (206, 220)      1  0.00421941
 339 │ fca37   (208, 218)      1  0.00421941
 340 │ fca37   (184, 184)      3  0.0126582
 341 │ fca37   (208, 210)      3  0.0126582
                             333 rows omitted

julia> genofreqtable(cats, by = "population")
1094×5 DataFrame
  Row │ locus   population  genotype    count  frequency         
      │ String  String      Tuple…      Int64  Float64           
──────┼──────────────────────────────────────────────────        
    1 │ fca8    1           (135, 143)      3  0.375
    2 │ fca8    1           (133, 135)      2  0.25
    3 │ fca8    1           (135, 135)      2  0.25
    4 │ fca8    1           (137, 143)      1  0.125
  ⋮   │   ⋮         ⋮           ⋮         ⋮        ⋮
 1091 │ fca37   17          (208, 208)     10  0.769231
 1092 │ fca37   17          (182, 182)      1  0.0769231
 1093 │ fca37   17          (182, 208)      1  0.0769231
 1094 │ fca37   17          (208, 220)      1  0.0769231
                                        1086 rows omitted 
```
