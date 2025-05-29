CDMテーブル名: DEVICE_EXPOSURE

Julia構造体名: DeviceExposure

```julia
struct DeviceExposure <: OMOPCommonDataModel.CDMType
```

  * `device_exposure_id::Int64`
  * `person_id::Int64`
  * `device_concept_id::Int64`
  * `device_exposure_start_date::Dates.DateTime`
  * `device_exposure_start_datetime::Union{Missing, Dates.DateTime}`
  * `device_exposure_end_date::Union{Missing, Dates.DateTime}`
  * `device_exposure_end_datetime::Union{Missing, Dates.DateTime}`
  * `device_type_concept_id::Int64`
  * `unique_device_id::Union{Missing, String}`
  * `quantity::Union{Missing, Int64}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `device_source_value::Union{Missing, String}`
  * `device_source_concept_id::Union{Missing, Int64}`
