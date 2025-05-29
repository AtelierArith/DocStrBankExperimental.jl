CDM table name: COHORT_DEFINITION

Julia struct name: CohortDefinition

```julia
struct CohortDefinition <: OMOPCommonDataModel.CDMType
```

  * `cohort_definition_id::Int64`
  * `cohort_definition_name::String`
  * `cohort_definition_description::Union{Missing, String}`
  * `definition_type_concept_id::Int64`
  * `cohort_definition_syntax::Union{Missing, String}`
  * `subject_concept_id::Int64`
  * `cohort_initiation_date::Union{Missing, Dates.DateTime}`
