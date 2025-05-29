```
highlight_search(lines::Vector{T}, search_matches::Dict{Int, Vector{Tuple{Int, Int}}}; kwargs...) where T <: AbstractString -> String
highlight_search(lines::Vector{T}, regex::Regex]; kwargs...) where T <: AbstractString -> String
```

`search_matches`（[`string_search_per_line`](@ref）を参照）でハイライトされた`lines`から構成されるテキストを返します。`search_matches`の代わりに`regex`が渡された場合、後者は[`string_search_per_line`](@ref)を使用して自動的に計算されます。

# キーワード

  * `active_match::Int`: アクティブと見なされるマッチ番号。このマッチは`highlight`の代わりに`active_highlight`を使用してハイライトされます。   (**デフォルト** = 0)
  * `active_highlight::String`: アクティブハイライトの装飾を含むANSIエスケープシーケンス。   (**デフォルト** = `\e[30;43m`.)
  * `end_line::Int`: 処理を終了する行。0以下の場合、すべての行が処理されます。   (**デフォルト** = 0)
  * `highlight::String`: ハイライトの装飾を含むANSIエスケープシーケンス。   (**デフォルト** = `\e[7m`)
  * `max_column::Int`: マッチがこの列の後にある場合、処理を停止します。0以下の場合、この制限は考慮されません。   (**デフォルト** = 0)
  * `min_column::Int`: この列の前のマッチは処理しません。0以下の場合、この制限は考慮されません。   (**デフォルト** = 0)
  * `start_line::Int`: 処理を開始する行。   (**デフォルト** = 1)
