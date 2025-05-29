```julia
templates_per_tech(
    systems::Array{Santiago.System}
) -> Dict{String, Set{String}}

```

すべての技術（ソースを含む）について、それが使用されたシステムテンプレートのリストを作成します。注意：少なくとも1つのシステムで使用されている技術のみがリストされます。
