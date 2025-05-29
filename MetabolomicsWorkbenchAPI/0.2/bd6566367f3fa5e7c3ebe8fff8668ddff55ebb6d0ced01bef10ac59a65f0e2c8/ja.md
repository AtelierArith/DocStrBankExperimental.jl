```
fetch_properties(metabolite_names::Vector{String}) => DataFrame
```

次の情報を含むデータフレームを返します: 正確な質量、式、主クラス、refmet名、副クラス、スーパークラス。

# 例:

```
julia> vNames = ["LPC(16:0p)", "PC(18:0p/18:1(9Z))", "CE(18:0)", "PC(O-32:1)", "TG(O-52:2)"];
julia> fetch_properties(vNames)
5×6 DataFrame
 Row │ exactmass  formula     main_class              refmet_name         sub_class     super_class
     │ String?    String?     String                  String                String        String
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 479.3376   C24H50NO6P  Glycerophosphocholines  LPC P-16:0            O-LPC         Glycerophospholipids
   2 │ missing    missing     Glycerophosphocholines  PC  P-18:0/18:1(9Z)*  PC            Glycerophospholipids
   3 │ 652.6158   C45H80O2    Sterol esters           CE 18:0               Chol. esters  Sterol Lipids
   4 │ 717.5672   C40H80NO7P  Glycerophosphocholines  PC O-32:1             O-PC          Glycerophospholipids
   5 │ missing    missing     Triradylglycerols       TG  O-52:2*           O-TAG         Glycerolipids
```
