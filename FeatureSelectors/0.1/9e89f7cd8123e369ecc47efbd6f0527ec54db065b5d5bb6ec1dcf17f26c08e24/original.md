```
one_hot_encode(df::DataFrame;
               cols::Vector{Symbol}=Vector{Symbol}(),
               drop_original::Bool=false)
```

Utility function to perform one-hot-encoding in DataFrame. This will add new columns with names `<original_col_name>_<value>`.

Following options can be passed to modify behavior.

  * `cols` - Vector of Symbol to specify which columns to be encoded. Defaults to empty, which means all features will be encoded.
  * `drop_original` - If true, this will drop the original feature set from resulting DataFrame. This defaults to false.

# Example

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
