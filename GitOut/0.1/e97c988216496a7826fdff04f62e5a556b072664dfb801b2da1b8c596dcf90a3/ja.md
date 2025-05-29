```julia
remotenames(
    r::GitOut.Repo;
    kw...
) -> Vector{SubString{String}}

```

リモートの名前のリストを `AbstractVector` の `AbstractString` として取得します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
