CDM table name: NOTE_NLP

Julia struct name: NoteNlp

```julia
struct NoteNlp <: OMOPCommonDataModel.CDMType
```

  * `note_nlp_id::Int64`
  * `note_id::Int64`
  * `section_concept_id::Union{Missing, Int64}`
  * `snippet::Union{Missing, String}`
  * `offset::Union{Missing, String}`
  * `lexical_variant::String`
  * `note_nlp_concept_id::Union{Missing, Int64}`
  * `note_nlp_source_concept_id::Union{Missing, Int64}`
  * `nlp_system::Union{Missing, String}`
  * `nlp_date::Dates.DateTime`
  * `nlp_datetime::Union{Missing, Dates.DateTime}`
  * `term_exists::Union{Missing, String}`
  * `term_temporal::Union{Missing, String}`
  * `term_modifiers::Union{Missing, String}`
