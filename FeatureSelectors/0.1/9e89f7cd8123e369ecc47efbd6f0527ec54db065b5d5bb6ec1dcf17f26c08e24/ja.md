```
one_hot_encode(df::DataFrame;
               cols::Vector{Symbol}=Vector{Symbol}(),
               drop_original::Bool=false)
```

DataFrameでワンホットエンコーディングを実行するためのユーティリティ関数です。これにより、`<original_col_name>_<value>`という名前の新しい列が追加されます。

動作を変更するために渡すことができるオプションは次のとおりです。

  * `cols` - エンコードする列を指定するためのSymbolのベクター。デフォルトは空で、すべての特徴がエンコードされることを意味します。
  * `drop_original` - trueの場合、結果のDataFrameから元の特徴セットが削除されます。デフォルトはfalseです。

# 例

```jldoctest
julia> using RDatasets, FeatureSelectors

julia> titanic = dataset("datasets", "Titanic");

julia> first(one_hot_encode(titanic[:, [:Class, :Sex, :Age]]), 3)
3×11 DataFrame
 Row │ Class    Sex      Age      Class_1st  Class_2nd  Class_3rd  Class_Crew  ⋯
     │ String7  String7  String7  Bool       Bool       Bool       Bool        ⋯
─────┼──────────────────────────────────────────────────────────────────────────
   1 │ 1st      Male     Child         true      false      false       false  ⋯
   2 │ 2nd      Male     Child        false       true      false       false
   3 │ 3rd      Male     Child        false      false       true       false
                                                               4 columns omitted


julia> first(one_hot_encode(titanic[:, [:Class, :Sex, :Age]], cols=[:Class], drop_original=true), 3)
3×6 DataFrame
 Row │ Sex      Age      Class_1st  Class_2nd  Class_3rd  Class_Crew
     │ String7  String7  Bool       Bool       Bool       Bool
─────┼───────────────────────────────────────────────────────────────
   1 │ Male     Child         true      false      false       false
   2 │ Male     Child        false       true      false       false
   3 │ Male     Child        false      false       true       false

```
