```
fit_string_in_field(str::AbstractString, field_width::Int; kwargs...) -> String
```

文字列 `str` を幅 `field_width` のフィールドに収まるように切り詰めます。

# キーワード

  * `add_continuation_char::Bool`: `true` の場合、切り詰めた文字列の末尾に継続文字が追加されます。返される文字列は常に印刷可能な幅 `field_size` を持つことに注意してください。   (**デフォルト** = `true`)
  * `add_space_in_continuation_char::Bool`: `true` の場合、`crop_size` が `:right` のときは継続文字の前にスペースが追加され、`crop_side` が `:left` のときは継続文字の後にスペースが追加されます。   (**デフォルト** = `false`)
  * `continuation_char::Char`: 文字列が切り詰められた場合に追加する継続文字です。   (**デフォルト** = `…`)
  * `crop_side::Symbol`: 文字をどの側から削除して文字列をフィールドに収めるかを選択します。`：right` または `:left` です。   (**デフォルト** = `:right`)
  * `field_margin::Int`: 切り詰める必要がある場合、フィールドに追加のマージンを考慮します。   (**デフォルト** = 0)
  * `keep_escape_seq::Bool`: `true` の場合、切り詰めた部分に見つかった ANSI エスケープシーケンスが保持されます。   (**デフォルト** = `true`)
  * `printable_string_width::Int`: 計算負担を軽減するために印刷可能な文字列の幅を提供します。このパラメータが 0 未満の場合、印刷可能な幅は内部で計算されます。   (**デフォルト** = -1)

# 拡張ヘルプ

## 例

```julia-repl
julia> fit_string_in_field("This is a very long string for a very small field", 10)
"This is a…"

julia> fit_string_in_field("This is a very long string for a very small field", 10; crop_side = :left)
"…all field"
```
