CDM table name: PAYER*PLAN*PERIOD

Julia struct name: PayerPlanPeriod

```julia
struct PayerPlanPeriod <: OMOPCommonDataModel.CDMType
```

  * `payer_plan_period_id::Int64`
  * `person_id::Int64`
  * `payer_plan_period_start_date::Dates.DateTime`
  * `payer_plan_period_end_date::Dates.DateTime`
  * `payer_concept_id::Union{Missing, Int64}`
  * `payer_source_value::Union{Missing, String}`
  * `payer_source_concept_id::Union{Missing, Int64}`
  * `plan_concept_id::Union{Missing, Int64}`
  * `plan_source_value::Union{Missing, String}`
  * `plan_source_concept_id::Union{Missing, Int64}`
  * `sponsor_concept_id::Union{Missing, Int64}`
  * `sponsor_source_value::Union{Missing, String}`
  * `sponsor_source_concept_id::Union{Missing, Int64}`
  * `family_source_value::Union{Missing, String}`
  * `stop_reason_concept_id::Union{Missing, Int64}`
  * `stop_reason_source_value::Union{Missing, String}`
  * `stop_reason_source_concept_id::Union{Missing, Int64}`
