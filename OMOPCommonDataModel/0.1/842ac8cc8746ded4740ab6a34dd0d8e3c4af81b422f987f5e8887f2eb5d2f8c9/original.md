CDM table name: CONDITION_OCCURRENCE

Julia struct name: ConditionOccurrence

```julia
struct ConditionOccurrence <: OMOPCommonDataModel.CDMType
```

  * `condition_occurrence_id::Int64`
  * `person_id::Int64`
  * `condition_concept_id::Int64`
  * `condition_start_date::Dates.DateTime`
  * `condition_start_datetime::Union{Missing, Dates.DateTime}`
  * `condition_end_date::Union{Missing, Dates.DateTime}`
  * `condition_end_datetime::Union{Missing, Dates.DateTime}`
  * `condition_type_concept_id::Int64`
  * `stop_reason::Union{Missing, String}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `condition_source_value::Union{Missing, String}`
  * `condition_source_concept_id::Union{Missing, Int64}`
  * `condition_status_source_value::Union{Missing, String}`
  * `condition_status_concept_id::Union{Missing, Int64}`
