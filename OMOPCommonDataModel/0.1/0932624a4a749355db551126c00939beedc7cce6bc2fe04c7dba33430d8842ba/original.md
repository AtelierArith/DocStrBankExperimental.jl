CDM table name: DRUG_ERA

Julia struct name: DrugEra

```julia
struct DrugEra <: OMOPCommonDataModel.CDMType
```

  * `drug_era_id::Int64`
  * `person_id::Int64`
  * `drug_concept_id::Int64`
  * `drug_era_start_date::Dates.DateTime`
  * `drug_era_end_date::Dates.DateTime`
  * `drug_exposure_count::Union{Missing, Int64}`
  * `gap_days::Union{Missing, Int64}`
