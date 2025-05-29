CDMテーブル名: VISIT_OCCURRENCE

Julia構造体名: VisitOccurrence

```julia
struct VisitOccurrence <: OMOPCommonDataModel.CDMType
```

  * `visit_occurrence_id::Int64`
  * `person_id::Int64`
  * `visit_concept_id::Int64`
  * `visit_start_date::Dates.DateTime`
  * `visit_start_datetime::Union{Missing, Dates.DateTime}`
  * `visit_end_date::Dates.DateTime`
  * `visit_end_datetime::Union{Missing, Dates.DateTime}`
  * `visit_type_concept_id::Int64`
  * `provider_id::Union{Missing, Int64}`
  * `care_site_id::Union{Missing, Int64}`
  * `visit_source_value::Union{Missing, String}`
  * `visit_source_concept_id::Union{Missing, Int64}`
  * `admitting_source_concept_id::Union{Missing, Int64}`
  * `admitting_source_value::Union{Missing, String}`
  * `discharge_to_concept_id::Union{Missing, Int64}`
  * `discharge_to_source_value::Union{Missing, String}`
  * `preceding_visit_occurrence_id::Union{Missing, Int64}`
