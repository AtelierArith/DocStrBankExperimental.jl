CDMテーブル名: PERSON

Julia構造体名: Person

```julia
struct Person <: OMOPCommonDataModel.CDMType
```

  * `person_id::Int64`
  * `gender_concept_id::Int64`
  * `year_of_birth::Int64`
  * `month_of_birth::Union{Missing, Int64}`
  * `day_of_birth::Union{Missing, Int64}`
  * `birth_datetime::Union{Missing, Dates.DateTime}`
  * `race_concept_id::Int64`
  * `ethnicity_concept_id::Int64`
  * `location_id::Union{Missing, Int64}`
  * `provider_id::Union{Missing, Int64}`
  * `care_site_id::Union{Missing, Int64}`
  * `person_source_value::Union{Missing, String}`
  * `gender_source_value::Union{Missing, String}`
  * `gender_source_concept_id::Union{Missing, Int64}`
  * `race_source_value::Union{Missing, String}`
  * `race_source_concept_id::Union{Missing, Int64}`
  * `ethnicity_source_value::Union{Missing, String}`
  * `ethnicity_source_concept_id::Union{Missing, Int64}`
