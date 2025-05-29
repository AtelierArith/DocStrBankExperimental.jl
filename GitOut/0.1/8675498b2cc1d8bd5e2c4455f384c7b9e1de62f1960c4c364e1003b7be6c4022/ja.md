```julia
listcommits(
    r::GitOut.Repo;
    ...
) -> Vector{SubString{String}}
listcommits(
    r::GitOut.Repo,
    n::Union{Nothing, Integer};
    branch,
    kw...
) -> Vector{SubString{String}}

```

リポジトリ `r` のコミットハッシュ（文字列として）を含む配列を返します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
