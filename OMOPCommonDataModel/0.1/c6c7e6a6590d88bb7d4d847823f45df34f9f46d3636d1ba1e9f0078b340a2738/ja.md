CDMテーブル名: SOURCE*TO*CONCEPT_MAP

Julia構造体名: SourceToConceptMap

```julia
struct SourceToConceptMap <: OMOPCommonDataModel.CDMType
```

  * `source_code::String`
  * `source_concept_id::Int64`
  * `source_vocabulary_id::String`
  * `source_code_description::Union{Missing, String}`
  * `target_concept_id::Int64`
  * `target_vocabulary_id::String`
  * `valid_start_date::Dates.DateTime`
  * `valid_end_date::Dates.DateTime`
  * `invalid_reason::Union{Missing, String}`
