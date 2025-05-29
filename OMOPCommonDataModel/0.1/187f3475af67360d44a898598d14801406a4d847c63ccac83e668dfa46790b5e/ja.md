CDMテーブル名: DRUG_EXPOSURE

Julia構造体名: DrugExposure

```julia
struct DrugExposure <: OMOPCommonDataModel.CDMType
```

  * `drug_exposure_id::Int64`
  * `person_id::Int64`
  * `drug_concept_id::Int64`
  * `drug_exposure_start_date::Dates.DateTime`
  * `drug_exposure_start_datetime::Union{Missing, Dates.DateTime}`
  * `drug_exposure_end_date::Dates.DateTime`
  * `drug_exposure_end_datetime::Union{Missing, Dates.DateTime}`
  * `verbatim_end_date::Union{Missing, Dates.DateTime}`
  * `drug_type_concept_id::Int64`
  * `stop_reason::Union{Missing, String}`
  * `refills::Union{Missing, Int64}`
  * `quantity::Union{Missing, Float64}`
  * `days_supply::Union{Missing, Int64}`
  * `sig::Union{Missing, String}`
  * `route_concept_id::Union{Missing, Int64}`
  * `lot_number::Union{Missing, String}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `drug_source_value::Union{Missing, String}`
  * `drug_source_concept_id::Union{Missing, Int64}`
  * `route_source_value::Union{Missing, String}`
  * `dose_unit_source_value::Union{Missing, String}`
