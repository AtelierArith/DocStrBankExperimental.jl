Generate JSON-able object representing an ACSet schema.

Given an ACSet schema (either a `Schema` or a `Presentation`), such as `SchGraph` or `SchWeightedGraph`, construct a JSON-able dictionary with keys "Ob", "Hom", "AttrType", and "Attr", conforming to the JSON Schema in [`acset_schema_json_schema`](@ref).

Inverse to [`parse_json_acset_schema`](@ref).
