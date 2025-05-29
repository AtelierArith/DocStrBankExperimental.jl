CDMテーブル名: ATTRIBUTE_DEFINITION

Julia構造体名: AttributeDefinition

```julia
struct AttributeDefinition <: OMOPCommonDataModel.CDMType
```

  * `attribute_definition_id::Int64`
  * `attribute_name::String`
  * `attribute_description::Union{Missing, String}`
  * `attribute_type_concept_id::Int64`
  * `attribute_syntax::Union{Missing, String}`
