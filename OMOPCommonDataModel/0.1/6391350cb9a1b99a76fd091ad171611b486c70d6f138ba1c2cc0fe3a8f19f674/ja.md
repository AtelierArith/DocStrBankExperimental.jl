CDMテーブル名: RELATIONSHIP

Julia構造体名: Relationship

```julia
struct Relationship <: OMOPCommonDataModel.CDMType
```

  * `relationship_id::String`
  * `relationship_name::String`
  * `is_hierarchical::String`
  * `defines_ancestry::String`
  * `reverse_relationship_id::String`
  * `relationship_concept_id::Int64`
