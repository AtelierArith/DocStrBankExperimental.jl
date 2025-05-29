```
align_string_per_line(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> String
```

文字列 `str` の各行を、`alignment` を使用して幅 `field_width` のフィールドに整列させます。`alignment` は次のいずれかです：

  * `:l`: 文字列を左に整列させる;
  * `:c`: 文字列を中央に整列させる;
  * `:r`: 文字列を右に整列させる。

!!! note
    `str` の印刷可能な幅が `field_width` より大きい場合、何も変更されません。


# キーワード

  * `fill::Bool`: `true` の場合、初期の文字列の印刷可能な幅がそれより小さい場合、結果の文字列が印刷可能な幅 `field_size` になるように、文字列の右側にスペースが埋められます。   (**デフォルト** = `false`)

# 拡張ヘルプ

## 例

```julia-repl
julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :c) |> println
                                      This is a string
                                       with multiple
                                           lines.

julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :l) |> println
This is a string
with multiple
lines.

julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :r) |> println
                                                                            This is a string
                                                                               with multiple
                                                                                      lines.
```
