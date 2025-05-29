CDMテーブル名: CONCEPT_ANCESTOR

Julia構造体名: ConceptAncestor

```julia
struct ConceptAncestor <: OMOPCommonDataModel.CDMType
```

  * `ancestor_concept_id::Int64`
  * `descendant_concept_id::Int64`
  * `min_levels_of_separation::Int64`
  * `max_levels_of_separation::Int64`
