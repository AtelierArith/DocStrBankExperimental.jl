CDM table name: COHORT_ATTRIBUTE

Julia struct name: CohortAttribute

```julia
struct CohortAttribute <: OMOPCommonDataModel.CDMType
```

  * `cohort_definition_id::Int64`
  * `subject_id::Int64`
  * `cohort_start_date::Dates.DateTime`
  * `cohort_end_date::Dates.DateTime`
  * `attribute_definition_id::Int64`
  * `value_as_number::Union{Missing, Float64}`
  * `value_as_concept_id::Union{Missing, Int64}`
