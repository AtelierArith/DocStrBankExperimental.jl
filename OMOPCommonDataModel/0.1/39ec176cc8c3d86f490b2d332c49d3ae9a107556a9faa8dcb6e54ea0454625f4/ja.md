CDMテーブル名: CONCEPT

Julia構造体名: Concept

```julia
struct Concept <: OMOPCommonDataModel.CDMType
```

  * `concept_id::Int64`
  * `concept_name::String`
  * `domain_id::String`
  * `vocabulary_id::String`
  * `concept_class_id::String`
  * `standard_concept::Union{Missing, String}`
  * `concept_code::String`
  * `valid_start_date::Dates.DateTime`
  * `valid_end_date::Dates.DateTime`
  * `invalid_reason::Union{Missing, String}`
