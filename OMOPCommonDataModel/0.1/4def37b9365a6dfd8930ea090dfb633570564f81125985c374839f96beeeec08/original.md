CDM table name: PROVIDER

Julia struct name: Provider

```julia
struct Provider <: OMOPCommonDataModel.CDMType
```

  * `provider_id::Int64`
  * `provider_name::Union{Missing, String}`
  * `NPI::Union{Missing, String}`
  * `DEA::Union{Missing, String}`
  * `specialty_concept_id::Union{Missing, Int64}`
  * `care_site_id::Union{Missing, Int64}`
  * `year_of_birth::Union{Missing, Int64}`
  * `gender_concept_id::Union{Missing, Int64}`
  * `provider_source_value::Union{Missing, String}`
  * `specialty_source_value::Union{Missing, String}`
  * `specialty_source_concept_id::Union{Missing, Int64}`
  * `gender_source_value::Union{Missing, String}`
  * `gender_source_concept_id::Union{Missing, Int64}`
