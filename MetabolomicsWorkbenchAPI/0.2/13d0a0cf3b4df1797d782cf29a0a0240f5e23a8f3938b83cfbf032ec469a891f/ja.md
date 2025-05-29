```
fetch_study_info(studyname::String) => DataFrame
```

利用可能な研究情報を含むデータフレームを返します。情報には研究タイトル、要約、研究所名、被験者の総数などが含まれます。

# 例:

```
julia> df = fetch_study_info("ST000001");
julia> select(dftest, [:STUDY_TITLE, :INSTITUTE])
1×2 DataFrame
 Row │ STUDY_TITLE                        INSTITUTE
     │ String                             String
─────┼────────────────────────────────────────────────────────────────────
   1 │ Fatb Induction Experiment (FatBI…  University of California, Davis                                                                                                                                                                                5 columns and 615 rows omitted
```
