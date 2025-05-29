```
sh_add(env_name::AbstractString; depot = first(DEPOT_PATH)) -> Vector{String}
sh_add(env_names::AbstractVector{<:AbstractString}; depot = first(DEPOT_PATH)) -> Vector{String}
sh_add(env_name::AbstractString, ARGS...; depot = first(DEPOT_PATH)) -> Vector{String}
```

共有環境を `LOAD_PATH` に追加し、対応するパッケージをすべて現在のセッションで利用可能にします。

追加された環境内のすべてのパッケージのリストを `Vector{String}` として返します。

# 例

```julia-repl
julia> using ShareAdd: sh_add
julia> sh_add("@StatPackages")
3-element Vector{String}:
 "Arrow"
 "CSV"
 "DataFrames"

julia> sh_add(["@StatPackages", "@Makie"])
4-element Vector{String}:
 "Arrow"
 "CSV"
 "DataFrames"
 "Makie"

julia> sh_add("@StatPackages", "@Makie")
4-element Vector{String}:
 "Arrow"
 "CSV"
 "DataFrames"
 "Makie"
```

この関数は公開されており、エクスポートされていません。
