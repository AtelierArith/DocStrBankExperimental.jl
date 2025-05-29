```
fetch_study_info(studyname::String) => DataFrame
```

Returns a dataframe containing the available study information such as the study title, summary, institute name, total number of subjects and much more.

# Example:

```
julia> df = fetch_study_info("ST000001");
julia> select(dftest, [:STUDY_TITLE, :INSTITUTE])
1×2 DataFrame
 Row │ STUDY_TITLE                        INSTITUTE
     │ String                             String
─────┼────────────────────────────────────────────────────────────────────
   1 │ Fatb Induction Experiment (FatBI…  University of California, Davis                                                                                                                                                                                5 columns and 615 rows omitted
```
