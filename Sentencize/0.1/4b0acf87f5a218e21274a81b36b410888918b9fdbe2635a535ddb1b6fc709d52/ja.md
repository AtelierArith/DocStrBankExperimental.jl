```
split_sentence(text::AbstractString; prefixes::Dict{<:AbstractString,PrefixType}=Dict{String,PrefixType}(), prefix_file::Union{String,Nothing}=nothing, lang::Union{String,Nothing}="en")
```

`text`を文に分割します。

# 引数

  * `text::AbstractString`: 文に分割するテキスト。
  * `prefixes::Dict{<:AbstractString,PrefixType}`: オプション。改行しない接頭辞の辞書。
  * `prefix_file::Union{String,Nothing}`: オプション。提供された`prefixes`に追加する改行しない接頭辞を含むファイルへのパス。
  * `lang::Union{String,Nothing}`: オプション。`prefixes`に追加される改行しない接頭辞の言語（利用可能な言語については`?SUPPORTED_LANG`を参照）。デフォルトは"en"（=英語）。

# 例

```julia
split_sentence("This is a paragraph. It contains several sentences. "But why," you ask?")
# 出力: ["This is a paragraph.", "It contains several sentences.", ""But why," you ask?"]
```
