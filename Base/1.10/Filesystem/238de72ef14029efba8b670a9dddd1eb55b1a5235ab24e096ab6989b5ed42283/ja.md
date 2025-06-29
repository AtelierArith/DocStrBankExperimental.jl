```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

名前 `path` の新しいディレクトリを作成し、権限 `mode` を設定します。`mode` はデフォルトで `0o777` であり、現在のファイル作成マスクによって変更されます。この関数は、1つのディレクトリ以上を作成することはありません。ディレクトリがすでに存在する場合、または中間ディレクトリのいずれかが存在しない場合、この関数はエラーをスローします。必要なすべての中間ディレクトリを作成する関数については、[`mkpath`](@ref) を参照してください。`path` を返します。

# 例

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
