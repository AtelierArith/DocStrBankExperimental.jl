```julia
init(
    dir::AbstractString;
    template,
    initial_branch,
    bare,
    shared,
    object_format,
    kw...
) -> GitOut.Repo

```

ディレクトリ `dir` を新しい git リポジトリとして初期化します。詳細は `man git init` を参照してください。追加のキーワード引数は [`rungit`](@ref) に渡されます。
