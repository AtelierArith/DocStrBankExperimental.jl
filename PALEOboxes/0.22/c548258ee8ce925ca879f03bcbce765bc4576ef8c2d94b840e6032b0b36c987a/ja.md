```
add_arrays_data!(
    model, modeldata, arrays_eltype::DataType, arrays_tagname::AbstractString;
    [method_barrier=nothing] [, generated_dispatch=true] [, kwargs...])
```

データ配列セットを `modeldata` に追加し、メモリを割り当て、reactiondataを初期化します。

要素の型とタグ名は `arrays_eltype`、`arrays_tagname` によって設定されます。

[`allocate_variables!(model::Model, modeldata::AbstractModelData, arrays_idx::Int)`](@ref) と [`initialize_reactiondata!`] のキーワード引数を参照してください。
