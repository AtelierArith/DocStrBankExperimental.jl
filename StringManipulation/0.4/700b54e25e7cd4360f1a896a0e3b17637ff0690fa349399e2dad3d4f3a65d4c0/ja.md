```
textview([io::IO,] text::AbstractString, view::NTuple{4, Int}; kwargs...)
textview([io::IO,] lines::Vector{AbstractString}, view::NTuple{4, Int}; kwargs...)
```

`text` または `lines` のビューを `view` 設定を考慮して作成します。後者は、次の意味を持つ4つの整数のタプルです。

  * 上部の行;
  * 行数;
  * 左の列; および
  * 列数。

これらのオプションのいずれかに0以下の値が渡された場合、その極端な値が使用されます。

# キーワード

  * `active_highlight::String`: アクティブハイライトの装飾を含むANSIエスケープシーケンス。 (**デフォルト** = `\e[30;43m`)
  * `active_match::Int`: アクティブと見なされる一致番号。この一致は、`highlight` の代わりに `active_highlight` を使用してハイライトされます。 (**デフォルト** = 0)
  * `frozen_columns_at_beginning::Int`: 最初に描画される凍結列の数。 (**デフォルト** = 0)
  * `frozen_lines_at_beginning::Int`: 最初に描画される凍結行の数。 (**デフォルト** = 0)
  * `highlight::String`: ハイライトの装飾を含むANSIエスケープシーケンス。 (**デフォルト** = `\e[7m`)
  * `maximum_number_of_columns::Int`: ビューの最大列数、ビューの幅に関係なく。-1の場合、ビューの幅全体が使用されます。 (**デフォルト** = -1)
  * `maximum_number_of_lines::Int`: ビューの最大行数、ビューの高さに関係なく。-1の場合、ビューの高さ全体が使用されます。 (**デフォルト** = -1)
  * `parse_decorations_before_view::Bool`: `true` の場合、ビューの前の行のすべての装飾をスキャンし、出力のレンダリング時に考慮します。そうでない場合、ビューの開始前のすべてが破棄されます。このオプションが `false` の場合、装飾が間違っている可能性があります。ただし、この機能は、入力文字列のサイズとビューの位置に応じて高い処理量を必要とする場合があります。 (**デフォルト** = `false`)
  * `ruler_decoration::String`: 定規の装飾を含むANSIエスケープシーケンス。 (**デフォルト** = `\e[90m`)
  * `show_ruler::Bool`: `true` の場合、ビューの左側に行番号のある定規が表示されます。 (**デフォルト** = `false`)
  * `visual_lines::Union{Nothing, Vector{Int}}`: 異なる背景でハイライトされる行の番号を含むベクター（ビジュアルモード）。`nothing` の場合、行は変更されません。 (**デフォルト** = `nothing`)
  * `visual_line_backgrounds::Union{String, Vector{String}}`: `visual_lines` の行の背景装飾のANSIコード。各行に対して背景を指定できる `Vector{String}` であるか、すべての背景が同じ装飾を持つ `String` であることができます。 (**デフォルト** = "44")
  * `title_lines::Int`: テキストの先頭にあるタイトルとして考慮される行数。つまり、ビューに関係なく画面に静的に印刷されます。 (**デフォルト** = 0)

`text::AbstractString` が渡された場合、次のキーワードが利用可能です。

  * `search_regex::Uniont{Nothing, Regex}`: テキストビュー内の一致をハイライトするために使用される正規表現。 (**デフォルト** = `nothing`).

`lines::Vector{AbstractString}` が渡された場合、次のキーワードが利用可能です。

  * `search_matches::Union{Nothing, Dict{Int, Vector{Tuple{Int, Int}}}}`: テキストビュー内でハイライトされる検索一致。この辞書は、関数 [`string_search_per_line`](@ref) を使用して作成する必要があります。 (**デフォルト** = `nothing`)

# 戻り値

`io` が渡された場合、ビューはそれに書き込まれ、関数は次の値を返します。

  * `Int`: 最後に切り取られた行の数。
  * `Int`: 行内で切り取られた最大文字数。

ただし、`io` が渡されない場合、関数は次の値を返します。

  * `String`: テキストビュー。
  * `Int`: 最後に切り取られた行の数。
  * `Int`: 行内で切り取られた最大文字数。

!!! note
    凍結行のみが印刷される場合、2番目の返される値は0に設定されます。

    凍結列のみが印刷される場合、3番目の返される値は0に設定されます。


```
