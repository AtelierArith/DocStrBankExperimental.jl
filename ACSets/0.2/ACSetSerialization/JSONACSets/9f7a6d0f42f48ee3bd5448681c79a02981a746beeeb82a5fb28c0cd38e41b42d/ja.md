ACSetスキーマを表すJSON可能なオブジェクトを生成します。

`Schema`または`Presentation`（例えば`SchGraph`や`SchWeightedGraph`）のACSetスキーマを与えられた場合、"Ob"、"Hom"、"AttrType"、および"Attr"というキーを持つJSON可能な辞書を構築します。これは[`acset_schema_json_schema`](@ref)のJSONスキーマに準拠します。

[`parse_json_acset_schema`](@ref)の逆です。
