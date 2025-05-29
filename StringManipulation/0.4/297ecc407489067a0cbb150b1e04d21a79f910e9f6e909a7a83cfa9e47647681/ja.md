```
crop_width_to_fit_string_in_field(str::AbstractString, field_width::Int; kwargs...) -> Int
```

フィールドのサイズ `field_width` に文字列 `str` が収まるように切り取るべき印刷可能な文字の数を取得します。

# キーワード

  * `add_continuation_char::Bool`: `true` の場合、切り取られた文字列の末尾に継続文字が追加されます。返される文字列は常に `field_size` の印刷可能な幅を持つことに注意してください。   (**デフォルト** = `true`)
  * `add_space_in_continuation_char::Bool`: `true` の場合、`crop_size` が `:right` の場合は継続文字の前にスペースが追加され、`crop_side` が `:left` の場合は継続文字の後にスペースが追加されます。   (**デフォルト** = `false`)
  * `continuation_char::Char`: 文字列が切り取られた場合に追加する継続文字。   (**デフォルト** = `…`)
  * `printable_string_width::Int`: 計算負担を軽減するために印刷可能な文字列の幅を提供します。このパラメータが 0 未満の場合、印刷可能な幅は内部で計算されます。   (**デフォルト** = -1)

# 拡張ヘルプ

## 例

```julia-repl
julia> crop_width_to_fit_string_in_field("This is a very long string for a very small field", 10)
40
```
