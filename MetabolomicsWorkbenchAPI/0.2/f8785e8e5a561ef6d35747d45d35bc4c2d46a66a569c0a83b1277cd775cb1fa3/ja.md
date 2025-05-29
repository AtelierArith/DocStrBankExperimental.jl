```
fetch_metabolites(studyname::String) => DataFrame
```

研究の代謝物の属性のデータフレームを返します。  

# 例:

```
julia> df = fetch_metabolites("ST001710");
julia> df[1:5,1:3]
5×10 DataFrame
 Row │ Metabolite           pubchem_id  inchi_key  kegg_id  other_id  other_id_type  ri      ri_type  moverz_quant
     │ String               String      String     String   String    String         String  String   String            String 
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ CE(16:0) + CE(18:1)                                                           9.12             369.351948452576
   2 │ CE(18:0)                                                                      9.64             369.351943579901
   3 │ CE(18:2)                                                                      8.71             369.351905113834
   4 │ CE(20:4)                                                                      8.48             369.351992746797
   5 │ Cer(d18:1/23:0)                                                               7.78             636.630358494506
```
