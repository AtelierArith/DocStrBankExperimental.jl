```julia
status(
    r::GitOut.Repo;
    ...
) -> Base.Generator{Base.EachLine{Base.GenericIOBuffer{SubArray{UInt8, 1, Vector{UInt8}, Tuple{UnitRange{Int64}}, true}}}, typeof(split)}
status(
    r::GitOut.Repo,
    pathspec::Union{Nothing, AbstractString};
    short,
    kw...
) -> Base.Generator{Base.EachLine{Base.GenericIOBuffer{SubArray{UInt8, 1, Vector{UInt8}, Tuple{UnitRange{Int64}}, true}}}, typeof(split)}

```

gitリポジトリ`r`のステータスを、`git status -s`の行の要素を含む配列として返します。追加のキーワード引数は[`rungit`](@ref)に渡されます。
