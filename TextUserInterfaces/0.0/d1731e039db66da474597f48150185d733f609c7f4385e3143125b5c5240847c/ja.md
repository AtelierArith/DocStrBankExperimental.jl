function create_menu(names::Vector{T1}, descriptions::Union{Nothing,Vector{T2}} = nothing; kwargs...)

メニューを作成します。名前は `names`、説明は `descriptions` です。`descriptions` が `nothing` または省略された場合、メニューの説明は表示されません。

# キーワード

  * `format`: `nothing` の場合、デフォルトのメニュー形式が使用されます。それ以外の場合、行数と列数をそれぞれ説明する2つの整数のタプルでなければなりません。(**デフォルト** = `nothing`)
  * `mark`: メニューのマーク。(**デフォルト** = `-`)
  * `one_value`: `true` の場合、メニューは複数の選択を持つことができません。(**デフォルト** = `true`)
  * `show_desc`: `true` の場合、メニューの説明が表示されます。(**デフォルト** = `true`)
  * `row_major`: `true` の場合、メニューは行優先の順序で構築されます。
  * `ignore_case`: `true` の場合、パターンマッチングで大文字と小文字は無視されます。
  * `show_match`: `true` の場合、パターンマッチング中にカーソルがアイテム名内に移動します。
  * `non_cyclic`: `true` の場合、メニューは非循環になります。
