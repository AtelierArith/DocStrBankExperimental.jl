```
padding_for_string_alignment(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> Union{Nothing, NTuple{2, Int}}
```

文字列 `str` を幅 `field_width` のフィールドに `alignment` を使用して整列させるために必要な左側と右側のパディングを返します。`alignment` は次のいずれかです：

  * `:l`: 文字列を左に整列させる;
  * `:c`: 文字列を中央に整列させる;
  * `:r`: 文字列を右に整列させる。

この関数は次の条件で `nothing` を返すことがあります：

1. 文字列を変更する必要がない場合;
2. 整列記号が不明な場合; または
3. `str` の印刷可能な幅が `field_width` より長い場合。

!!! note
    この関数は `\n` を通常の文字として扱います。


# キーワード

  * `fill::Bool`: `true` の場合、文字列は右側にスペースで埋められ、結果として得られる文字列の印刷可能な幅が `field_size` になるようにします。初期の文字列の印刷可能な幅がそれより小さい場合。   (**デフォルト** = `false`)
  * `printable_string_width::Int`: 計算負担を軽減するために印刷可能な文字列の幅を提供します。このパラメータが 0 より小さい場合、印刷可能な幅は内部で計算されます。   (**デフォルト** = -1)

# 拡張ヘルプ

## 例

```julia-repl
julia> padding_for_string_alignment("My string", 92, :c)
(41, 0)

julia> padding_for_string_alignment("My string", 92, :l)

julia> padding_for_string_alignment("My string", 92, :r)
(83, 0)
```
