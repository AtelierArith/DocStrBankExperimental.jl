```julia
remotes(
    r::GitOut.Repo;
    kw...
) -> Union{OrderedCollections.OrderedDict{Any, Any}, OrderedCollections.OrderedDict{SubString{String}}}

```

リポジトリ `r` のリモートを `OrderedDict` として取得します。キーはリモート名で、値はリモートのURLです。追加のキーワード引数は [`rungit`](@ref) に渡されます。
