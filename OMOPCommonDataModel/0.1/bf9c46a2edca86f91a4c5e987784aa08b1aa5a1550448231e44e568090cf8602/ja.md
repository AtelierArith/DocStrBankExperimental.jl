CDMテーブル名: DRUG_STRENGTH

Julia構造体名: DrugStrength

```julia
struct DrugStrength <: OMOPCommonDataModel.CDMType
```

  * `drug_concept_id::Int64`
  * `ingredient_concept_id::Int64`
  * `amount_value::Union{Missing, Float64}`
  * `amount_unit_concept_id::Union{Missing, Int64}`
  * `numerator_value::Union{Missing, Float64}`
  * `numerator_unit_concept_id::Union{Missing, Int64}`
  * `denominator_value::Union{Missing, Float64}`
  * `denominator_unit_concept_id::Union{Missing, Int64}`
  * `box_size::Union{Missing, Int64}`
  * `valid_start_date::Dates.DateTime`
  * `valid_end_date::Dates.DateTime`
  * `invalid_reason::Union{Missing, String}`
