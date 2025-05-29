CDMテーブル名: CARE_SITE

Julia構造体名: CareSite

```julia
struct CareSite <: OMOPCommonDataModel.CDMType
```

  * `care_site_id::Int64`
  * `care_site_name::Union{Missing, String}`
  * `place_of_service_concept_id::Union{Missing, Int64}`
  * `location_id::Union{Missing, Int64}`
  * `care_site_source_value::Union{Missing, String}`
  * `place_of_service_source_value::Union{Missing, String}`
