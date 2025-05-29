CDMテーブル名: CONDITION_ERA

Julia構造体名: ConditionEra

```julia
struct ConditionEra <: OMOPCommonDataModel.CDMType
```

  * `condition_era_id::Int64`
  * `person_id::Int64`
  * `condition_concept_id::Int64`
  * `condition_era_start_date::Dates.DateTime`
  * `condition_era_end_date::Dates.DateTime`
  * `condition_occurrence_count::Union{Missing, Int64}`
