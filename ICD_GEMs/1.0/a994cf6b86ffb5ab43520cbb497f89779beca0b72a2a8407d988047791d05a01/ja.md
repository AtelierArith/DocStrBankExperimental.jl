```
struct GEM{T <: Union{DataFrame, OrderedDict{String, OrderedDict{String, Any}}}}
```

**一般的な同等性マップ (GEM)** テーブルを表します。

# フィールド

  * `data<: Union{DataFrame,OrderedDict{String, OrderedDict{String, Any}}}`: 実際のGEMデータで、`get_gem_dataframe_from_cdc_gem_txt`または`get_GEM_dictionary_from_cdc_gem_txt`によって返されるため、`DataFrame`または`OrderedDict`のいずれかである可能性があります。
  * `direction::String`: `"I9_I10"`（ICD-9からICD-10）または`"I10_I9"`（ICD-10からICD-9）のいずれかです。
