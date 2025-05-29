CDMテーブル名: CONCEPT_RELATIONSHIP

Julia構造体名: ConceptRelationship

```julia
struct ConceptRelationship <: OMOPCommonDataModel.CDMType
```

  * `concept_id_1::Int64`
  * `concept_id_2::Int64`
  * `relationship_id::String`
  * `valid_start_date::Dates.DateTime`
  * `valid_end_date::Dates.DateTime`
  * `invalid_reason::Union{Missing, String}`
