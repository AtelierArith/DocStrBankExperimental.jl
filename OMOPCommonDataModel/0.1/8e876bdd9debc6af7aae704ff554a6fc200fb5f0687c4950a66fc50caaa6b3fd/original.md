CDM table name: DEATH

Julia struct name: Death

```julia
struct Death <: OMOPCommonDataModel.CDMType
```

  * `person_id::Int64`
  * `death_date::Dates.DateTime`
  * `death_datetime::Union{Missing, Dates.DateTime}`
  * `death_type_concept_id::Int64`
  * `cause_concept_id::Union{Missing, Int64}`
  * `cause_source_value::Union{Missing, String}`
  * `cause_source_concept_id::Union{Missing, Int64}`
