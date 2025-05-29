```
split_message(text::AbstractString; chunk_limit::UInt=2000,
              extrastyles::Vector{Regex}=Vector{Regex}(),
              forcesplit::Bool = true) -> Vector{String}
```

メッセージを、最大で `chunk_limit` の長さのチャンクに分割し、フォーマットを保持します。

`chunk_limit` のデフォルトは Discord のメッセージの 2000 文字制限ですが、任意の非負整数に変更できます。

フォーマットは [`STYLES`](@ref) によって指定され、`extrastyles` 引数で集約できます。

Discord はメッセージを 2000 に制限しているため、フォーマットの破損を避けられない場合はコードが強制的に分割します。ただし、望ましい場合は `forcesplit` を false に設定することでこの動作を解除できます。

## 例

```julia
julia> split_message("foo")
1-element Vector{String}:
 "foo"

julia> split_message(repeat('.', 1995) * "**hello, world**")[2]
"**hello, world**"

julia> split_message("**hello**, *world*", chunk_limit=10)
2-element Vector{String}:
 "**hello**,"
 "*world*"

julia> split_message("**hello**, _*beautiful* world_", chunk_limit=15)
┌ Warning: message was forced-split to fit the desired chunk length limit 15
└ @ Main REPL[66]:28
3-element Vector{String}:
 "**hello**,"
 "_*beautiful* wo"
 "rld_"

julia> split_message("**hello**, _*beautiful* world_", chunk_limit=15, forcesplit=false)
┌ Warning: message could not be split into chunks smaller than the length limit 15
└ @ Main REPL[66]:32
2-element Vector{String}:
 "**hello**,"
 "_*beautiful* world_"

julia> split_message("**hello**\n=====\n", chunk_limit=12)
2-element Vector{String}:
 "**hello**\n=="
 "==="

julia> split_message("**hello**\n≡≡≡≡≡\n", chunk_limit=12, extrastyles = [r"\n≡+\n"])
2-element Vector{String}:
 "**hello**"
 "≡≡≡≡≡"
```
