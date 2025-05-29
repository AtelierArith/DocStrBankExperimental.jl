```
fetch_samples(studyname::String) => DataFrame
```

Return the samples dataframe of the study.  

# Example:

```
julia> fetch_samples("ST001710")
627×15 DataFrame
 Row │ Sample ID   Data type         NAFLD.Category  T2DM    Kleiner.Steatosis  Inflammation  Sex     Sample_Data:Ballooning  Kleiner.Fibrosis  NAS     Platelets.E10-9.per.L  Liver.ALT  Liver.AST  AST.ALT.Ratio       ⋯     │ String      String            String          String  String             String        String  String                  String            String  String                 String     String     String              ⋯─────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────   1 │ 1022385746  Serum lipidomics  1               NA      1                  -             NA      -                       -                 1       235                    173        248        1.43352601156069    ⋯   2 │ 1022385747  Serum lipidomics  1               NA      1                  1             NA      -                       -                 2       278                    38         41         1.07894736842105     
   3 │ 1022385761  Serum lipidomics  1               NA      1                  1             NA      -                       -                 2       246                    22         27         1.22727272727273     
   4 │ 1022385792  Serum lipidomics  1               NA      1                  3             NA      -                       1c                3       283                    20         18         0.9
   5 │ 1022385816  Serum lipidomics  1               NA      2                  1             NA      -                       -                 3       280                    NA         NA         NA                  ⋯   6 │ 1022385825  Serum lipidomics  1               NA      2                  1             NA      -                       NA                3       252                    116        69         0.594827586206897    
  ⋮  ⋮              ⋮                ⋮           ⋮             ⋮               ⋮          ⋮               ⋮                    ⋮            ⋮               ⋮                ⋮          ⋮              ⋮           ⋱ 622 │ 1022386897  Serum lipidomics  NA              Y       NA                 NA            NA      NA                      NA                NA      267                    32         32         1
 623 │ 1026694057  Serum lipidomics  -               N       -                  -             NA      -                       -                 -       NA                     27         21         0.777777777777778    
 624 │ 1028937993  Serum lipidomics  -               N       -                  -             NA      NA                      -                 NA      NA                     26         27         1.03846153846154    ⋯ 625 │ 1028939944  Serum lipidomics  -               N       -                  -             NA      -                       -                 -       187                    29         26         0.896551724137931    
 626 │ 1026694049  Serum lipidomics  -               Y       -                  -             NA      -                       -                 -       NA                     18         20         1.11111111111111     
 627 │ 1022385827  Serum lipidomics  1               NA      1                  1             NA      -                       -                 2       NA                     35         22         0.628571428571429                                                                                                                                                
                                                                                                                                                                                            5 columns and 615 rows omitted
```
