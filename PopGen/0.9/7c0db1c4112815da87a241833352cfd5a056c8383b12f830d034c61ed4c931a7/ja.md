```
kinshipposthoc(::PopData, results::DataFrame; iterations::Int)
```

kinship()から得られたDataFrameまたはNamedTupleを使用して事後分析を実行します。この分析では、母集団内の親族関係が母集団間の親族関係よりも有意に高いかどうかをテストするために置換を使用します。`results`オブジェクトは、提供された`PopData`から生成されている必要があります。置換テストの反復回数を指定するには`iterations =`を使用します（デフォルト = `20000`）。**推奨**として、結果のP値を修正するために`MultipleTesting.jl`を使用してください。

**例**

```
julia> cats = @nancycats ;

julia> rel_out = kinship(cats, method = [Ritland, Moran], iterations = 100);

julia> kinshipposthoc(cats, rel_out)
17x3 DataFrame
 Row │ population  Ritland_P  Moran_P
     │ String      Float64    Float64
─────┼────────────────────────────────
   1 │ 1              5.0e-5   5.0e-5
   2 │ 2              5.0e-5   5.0e-5
   3 │ 3              5.0e-5   5.0e-5
   4 │ 4              5.0e-5   5.0e-5
   5 │ 5              5.0e-5   5.0e-5
   6 │ 6              5.0e-5   5.0e-5
   7 │ 7              5.0e-5   5.0e-5
   8 │ 8              5.0e-5   5.0e-5
   9 │ 9              5.0e-5   5.0e-5
  10 │ 10             5.0e-5   5.0e-5
  11 │ 11             5.0e-5   5.0e-5
  12 │ 12             5.0e-5   5.0e-5
  13 │ 13             5.0e-5   5.0e-5
  14 │ 14             5.0e-5   5.0e-5
  15 │ 15             5.0e-5   5.0e-5
  16 │ 16             5.0e-5   5.0e-5
  17 │ 17             5.0e-5   5.0e-5
```
