```
align_string(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> String
```

文字列 `str` を幅 `field_width` のフィールドに `alignment` を使用して整列します。`alignment` には以下のオプションがあります：

  * `:l`: 文字列を左に整列します；
  * `:c`: 文字列を中央に整列します；
  * `:r`: 文字列を右に整列します。

!!! note
    `str` の印刷可能な幅が `field_width` より大きい場合、何も変更されません。


!!! note
    この関数は `\n` を通常の文字として扱います。すべての行を整列させたい場合は、関数 [`align_string_per_line`](@ref) を使用してください。


# キーワード

  * `fill::Bool`: `true` の場合、文字列は右側にスペースで埋められ、結果として得られる文字列の印刷可能な幅が `field_size` になります。初期の文字列の印刷可能な幅がそれより小さい場合。   (**デフォルト** = `false`)
  * `printable_string_width::Int`: 計算負担を軽減するために印刷可能な文字列の幅を提供します。このパラメータが 0 より小さい場合、印刷可能な幅は内部で計算されます。   (**デフォルト** = -1)

# 拡張ヘルプ

## 例

```julia-repl
julia> align_string("My String", 92, :c) |> println
                                         My String

julia> align_string("My String", 92, :l) |> println
My String

julia> align_string("My String", 92, :r) |> println
                                                                                   My String
```
