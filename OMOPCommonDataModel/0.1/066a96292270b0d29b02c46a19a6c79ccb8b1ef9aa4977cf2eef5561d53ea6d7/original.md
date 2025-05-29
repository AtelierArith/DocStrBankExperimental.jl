CDM table name: DOSE_ERA

Julia struct name: DoseEra

```julia
struct DoseEra <: OMOPCommonDataModel.CDMType
```

  * `dose_era_id::Int64`
  * `person_id::Int64`
  * `drug_concept_id::Int64`
  * `unit_concept_id::Int64`
  * `dose_value::Float64`
  * `dose_era_start_date::Dates.DateTime`
  * `dose_era_end_date::Dates.DateTime`
