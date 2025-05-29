CDMテーブル名: SPECIMEN

Julia構造体名: Specimen

```julia
struct Specimen <: OMOPCommonDataModel.CDMType
```

  * `specimen_id::Int64`
  * `person_id::Int64`
  * `specimen_concept_id::Int64`
  * `specimen_type_concept_id::Int64`
  * `specimen_date::Dates.DateTime`
  * `specimen_datetime::Union{Missing, Dates.DateTime}`
  * `quantity::Union{Missing, Float64}`
  * `unit_concept_id::Union{Missing, Int64}`
  * `anatomic_site_concept_id::Union{Missing, Int64}`
  * `disease_status_concept_id::Union{Missing, Int64}`
  * `specimen_source_id::Union{Missing, String}`
  * `specimen_source_value::Union{Missing, String}`
  * `unit_source_value::Union{Missing, String}`
  * `anatomic_site_source_value::Union{Missing, String}`
  * `disease_status_source_value::Union{Missing, String}`
