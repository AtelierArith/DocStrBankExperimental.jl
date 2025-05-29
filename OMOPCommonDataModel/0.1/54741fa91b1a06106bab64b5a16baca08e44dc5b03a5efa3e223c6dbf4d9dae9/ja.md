CDMテーブル名: COHORT

Julia構造体名: Cohort

```julia
struct Cohort <: OMOPCommonDataModel.CDMType
```

  * `cohort_definition_id::Int64`
  * `subject_id::Int64`
  * `cohort_start_date::Dates.DateTime`
  * `cohort_end_date::Dates.DateTime`
