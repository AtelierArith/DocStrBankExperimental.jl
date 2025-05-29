CDM table name: MEASUREMENT

Julia struct name: Measurement

```julia
struct Measurement <: OMOPCommonDataModel.CDMType
```

  * `measurement_id::Int64`
  * `person_id::Int64`
  * `measurement_concept_id::Int64`
  * `measurement_date::Dates.DateTime`
  * `measurement_datetime::Union{Missing, Dates.DateTime}`
  * `measurement_time::Union{Missing, String}`
  * `measurement_type_concept_id::Int64`
  * `operator_concept_id::Union{Missing, Int64}`
  * `value_as_number::Union{Missing, Float64}`
  * `value_as_concept_id::Union{Missing, Int64}`
  * `unit_concept_id::Union{Missing, Int64}`
  * `range_low::Union{Missing, Float64}`
  * `range_high::Union{Missing, Float64}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `measurement_source_value::Union{Missing, String}`
  * `measurement_source_concept_id::Union{Missing, Int64}`
  * `unit_source_value::Union{Missing, String}`
  * `value_source_value::Union{Missing, String}`
