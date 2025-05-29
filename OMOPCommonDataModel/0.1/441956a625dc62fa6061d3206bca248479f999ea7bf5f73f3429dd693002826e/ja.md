CDMテーブル名: COST

Julia構造体名: Cost

```julia
struct Cost <: OMOPCommonDataModel.CDMType
```

  * `cost_id::Int64`
  * `cost_event_id::Int64`
  * `cost_domain_id::String`
  * `cost_type_concept_id::Int64`
  * `currency_concept_id::Union{Missing, Int64}`
  * `total_charge::Union{Missing, Float64}`
  * `total_cost::Union{Missing, Float64}`
  * `total_paid::Union{Missing, Float64}`
  * `paid_by_payer::Union{Missing, Float64}`
  * `paid_by_patient::Union{Missing, Float64}`
  * `paid_patient_copay::Union{Missing, Float64}`
  * `paid_patient_coinsurance::Union{Missing, Float64}`
  * `paid_patient_deductible::Union{Missing, Float64}`
  * `paid_by_primary::Union{Missing, Float64}`
  * `paid_ingredient_cost::Union{Missing, Float64}`
  * `paid_dispensing_fee::Union{Missing, Float64}`
  * `payer_plan_period_id::Union{Missing, Int64}`
  * `amount_allowed::Union{Missing, Float64}`
  * `revenue_code_concept_id::Union{Missing, Int64}`
  * `reveue_code_source_value::Union{Missing, String}`
  * `drg_concept_id::Union{Missing, Int64}`
  * `drg_source_value::Union{Missing, String}`
