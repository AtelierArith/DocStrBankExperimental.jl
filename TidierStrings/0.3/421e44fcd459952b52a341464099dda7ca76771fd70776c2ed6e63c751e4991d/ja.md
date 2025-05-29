str_trunc(string::AbstractString, width::Integer; side::String="right", ellipsis::AbstractString="...")

文字列を固定の文字数に切り詰めます。

# 引数

  * `string`: 切り詰める対象の入力文字列。
  * `width`: 結果の文字列の最大幅（省略記号を含む）。
  * `side`: 切り詰める側。 "right"、"left"、または "center" のいずれか。デフォルトは "right"。
  * `ellipsis`: 内容が削除されたことを示す文字列。デフォルトは "..."。

# 戻り値

省略記号を含めて `width` 以下の長さの切り詰められた文字列。

# 例

```jldoctest
julia> str_trunc("This is a long string", 10)
"This is..."

julia> str_trunc("This is a long string", 10, side="left")
"...g string"

julia> str_trunc("This is a long string", 10, side="center")
"Thi...ring"

julia> str_trunc("Short", 10)
"Short"

julia> str_trunc("This is a long string that needs to be truncated", 20, side = "right", ellipsis = "--")
"This is a long str--"
```
