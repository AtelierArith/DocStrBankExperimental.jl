CDM table name: NOTE

Julia struct name: Note

```julia
struct Note <: OMOPCommonDataModel.CDMType
```

  * `note_id::Int64`
  * `person_id::Int64`
  * `note_date::Dates.DateTime`
  * `note_datetime::Union{Missing, Dates.DateTime}`
  * `note_type_concept_id::Int64`
  * `note_class_concept_id::Int64`
  * `note_title::Union{Missing, String}`
  * `note_text::Union{Missing, String}`
  * `encoding_concept_id::Int64`
  * `language_concept_id::Int64`
  * `provider_id::Union{Missing, Int64}`
  * `visit_occurrence_id::Union{Missing, Int64}`
  * `visit_detail_id::Union{Missing, Int64}`
  * `note_source_value::Union{Missing, String}`
