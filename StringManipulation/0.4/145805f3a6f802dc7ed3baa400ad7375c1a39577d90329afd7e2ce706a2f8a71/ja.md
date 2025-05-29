```
highlight_search(str::AbstractString, search_matches::Vector{Tuple{Int, Int}}; kwargs...) -> String
highlight_search(str::AbstractString, regex::Regex; kwargs...) -> String
```

文字列 `str` の中で `search_matches`（[`string_search`](@ref) を参照）をハイライトしたテキストを返します。`search_matches` の代わりに `regex` が渡された場合、後者は自動的に [`string_search`](@ref) を使用して計算されます。

# キーワード

  * `active_match::Int`: アクティブと見なされるマッチ番号。このマッチは `highlight` の代わりに `active_highlight` を使用してハイライトされます。   (**デフォルト** = 0)
  * `active_highlight::String`: アクティブハイライトの装飾を含む ANSI エスケープシーケンス。   (**デフォルト** = `\e[30;43m`.)
  * `highlight::String`: ハイライトの装飾を含む ANSI エスケープシーケンス。   (**デフォルト** = `\e[7m`)
  * `max_column::Int`: マッチがこのカラムの後にある場合、処理を停止します。0以下の場合、この制限は考慮されません。   (**デフォルト** = 0)
  * `min_column::Int`: このカラムの前のマッチは処理しません。0以下の場合、この制限は考慮されません。   (**デフォルト** = 0)
  * `start_column::Int`: アルゴリズムは `str` の最初の文字がこのカラムにあると見なします。   (**デフォルト** = 1)
