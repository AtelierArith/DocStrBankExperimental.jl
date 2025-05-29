CDMテーブル名: OBSERVATION

Julia構造体名: Observation

```julia
struct Observation <: OMOPCommonDataModel.CDMType
```

  * `observation_id::Int64`
  * `person_id::Int64`
  * `observation_concept_id::Int64`
  * `observation_date::Dates.DateTime`
  * `observation_datetime::Union{Missing, Dates.DateTime}`
  * `observation_type_concept_id::Int64`
  * `value_as_number::Union{Missing, Float64}`
  * `value_as_string::Union{Missing, String}`
  * `value_as_concept_id::Union{Missing, Int64}`
  * `qualifier_concept_id::Union{Missing, Int64}`
  * `unit_concept_id::Union{Missing, Int64}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `observation_source_value::Union{Missing, String}`
  * `observation_source_concept_id::Union{Missing, Int64}`
  * `unit_source_value::Union{Missing, String}`
  * `qualifier_source_value::Union{Missing, String}`
