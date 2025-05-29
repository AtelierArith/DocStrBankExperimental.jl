CDMテーブル名: OBSERVATION_PERIOD

Julia構造体名: ObservationPeriod

```julia
struct ObservationPeriod <: OMOPCommonDataModel.CDMType
```

  * `observation_period_id::Int64`
  * `person_id::Int64`
  * `observation_period_start_date::Dates.DateTime`
  * `observation_period_end_date::Dates.DateTime`
  * `period_type_concept_id::Int64`
