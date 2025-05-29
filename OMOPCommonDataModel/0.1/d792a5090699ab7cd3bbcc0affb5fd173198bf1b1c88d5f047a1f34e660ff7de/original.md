CDM table name: PROCEDURE_OCCURRENCE

Julia struct name: ProcedureOccurrence

```julia
struct ProcedureOccurrence <: OMOPCommonDataModel.CDMType
```

  * `procedure_occurrence_id::Int64`
  * `person_id::Int64`
  * `procedure_concept_id::Int64`
  * `procedure_date::Dates.DateTime`
  * `procedure_datetime::Union{Missing, Dates.DateTime}`
  * `procedure_type_concept_id::Int64`
  * `modifier_concept_id::Union{Missing, Int64}`
  * `quantity::Union{Missing, Int64}`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `procedure_source_value::Union{Missing, String}`
  * `procedure_source_concept_id::Union{Missing, Int64}`
  * `modifier_source_value::Union{Missing, String}`
