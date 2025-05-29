```
right_crop(str::AbstractString, crop_width::Int; kwargs...) -> String, String
```

与えられたフィールドの印刷可能な幅 `crop_width` に基づいて、`str` の右側の文字を切り取ることによって得られる文字列を返します。

# 戻り値

  * `String`: 切り取られた文字列。
  * `String`: 切り取られた部分のANSIエスケープシーケンス（非印刷可能な文字列）。

# キーワード

  * `keep_escape_seq::Bool`: `false` の場合、切り取られたフィールドのANSIエスケープシーケンスは計算されません。この場合、返される2番目の引数は常に空になります。   (**デフォルト** = `true`)
  * `printable_string_width::Int`: 計算負担を軽減するために印刷可能な文字列の幅を提供します。このパラメータが0未満の場合、印刷可能な幅は内部で計算されます。 (**デフォルト** = -1)

!!! warning
    キーワード `keep_escape_seq` が `true` に設定されている場合、すべての文字列を処理する必要があり、計算時間が大幅に増加する可能性があります。


# 例

```julia-repl
julia> right_crop("[1mPlease, crop this [0mstring.", 8)
("[1mPlease, crop this", "[0m")

julia> right_crop("[1mPlease, crop this [0mstring.", 8; keep_escape_seq = false)
("[1mPlease, crop this", "")
```
