```
mv(src::AbstractString, dst::AbstractString; force::Bool=false)
```

ファイル、リンク、またはディレクトリを `src` から `dst` に移動します。 `force=true` は、最初に既存の `dst` を削除します。 `dst` を返します。

# 例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> write("hello.txt", "world");

julia> mv("hello.txt", "goodbye.txt")
"goodbye.txt"

julia> "hello.txt" in readdir()
false

julia> readline("goodbye.txt")
"world"

julia> write("hello.txt", "world2");

julia> mv("hello.txt", "goodbye.txt")
ERROR: ArgumentError: 'goodbye.txt' が存在します。 'goodbye.txt' を移動する前に削除するには `force=true` が必要です。
Stacktrace:
 [1] #checkfor_mv_cp_cptree#10(::Bool, ::Function, ::String, ::String, ::String) at ./file.jl:293
[...]

julia> mv("hello.txt", "goodbye.txt", force=true)
"goodbye.txt"

julia> rm("goodbye.txt");

```
