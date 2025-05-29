CDMテーブル名: VISIT_DETAIL

Julia構造体名: VisitDetail

```julia
struct VisitDetail <: OMOPCommonDataModel.CDMType
```

  * `visit_detail_id::Int64`
  * `person_id::Int64`
  * `visit_detail_concept_id::Int64`
  * `visit_detail_start_date::Dates.DateTime`
  * `visit_detail_start_datetime::Union{Missing, Dates.DateTime}`
  * `visit_detail_end_date::Dates.DateTime`
  * `visit_detail_end_datetime::Union{Missing, Dates.DateTime}`
  * `visit_detail_type_concept_id::Int64`
  * `provider_id::Union{Missing, Int64}`
  * `care_site_id::Union{Missing, Int64}`
  * `admitting_source_concept_id::Union{Missing, Int64}`
  * `discharge_to_concept_id::Union{Missing, Int64}`
  * `preceding_visit_detail_id::Union{Missing, Int64}`
  * `visit_detail_source_value::Union{Missing, String}`
  * `visit_detail_source_concept_id::Union{Missing, Int64}`
  * `admitting_source_value::Union{Missing, String}`
  * `discharge_to_source_value::Union{Missing, String}`
  * `visit_detail_parent_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Int64`
