```
str_wrap(string::AbstractString; width::Integer=80, indent::Integer=0, exdent::Integer=0, whitespace_only::Bool=true)::String
```

文字列を複数行にラップします。

引数

  * `string`: 入力文字列。
  * `width`: 各行の最大幅。デフォルトは80。
  * `indent`: 各行をインデントするスペースの数。デフォルトは0。
  * `exdent`: 各行を外側にインデントするスペースの数。デフォルトは0。
  * `whitespace_only`: 空白のみでラップするかどうか。デフォルトはtrue。

ラップされた文字列を返します。

例

```jldoctest
julia> println(str_wrap("This is an example text that should be wrapped based on the given width and breaking rules.", width=20))
This is an example
text that should be
wrapped based on the
given width and
breaking rules.
```
