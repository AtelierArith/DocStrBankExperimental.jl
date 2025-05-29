CDMテーブル名: CDM_SOURCE

Julia構造体名: CdmSource

```julia
struct CdmSource <: OMOPCommonDataModel.CDMType
```

  * `cdm_source_name::String`
  * `cdm_source_abbreviation::Union{Missing, String}`
  * `cdm_holder::Union{Missing, String}`
  * `source_description::Union{Missing, String}`
  * `source_documentation_reference::Union{Missing, String}`
  * `cdm_etl_reference::Union{Missing, String}`
  * `source_release_date::Union{Missing, Dates.DateTime}`
  * `cdm_release_date::Union{Missing, Dates.DateTime}`
  * `cdm_version::Union{Missing, String}`
  * `vocabulary_version::Union{Missing, String}`
