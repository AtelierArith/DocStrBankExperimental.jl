CDMテーブル名: METADATA

Julia構造体名: Metadata

```julia
struct Metadata <: OMOPCommonDataModel.CDMType
```

  * `metadata_concept_id::Int64`
  * `metadata_type_concept_id::Int64`
  * `name::String`
  * `value_as_string::Union{Missing, String}`
  * `value_as_concept_id::Union{Missing, Int64}`
  * `metadata_date::Union{Missing, Dates.DateTime}`
  * `metadata_datetime::Union{Missing, Dates.DateTime}`
