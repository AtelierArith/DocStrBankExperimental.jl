```
str_to_sentence(s::AbstractString)
```

文字列内の各文の最初の文字を大文字に変換します。

引数

  * `s`: 入力文字列。

戻り値 各文の最初の文字が大文字に変換された文字列。

例

```jldoctest
julia> str_to_sentence("hello world!")
"Hello world!"

julia> str_to_sentence("a sentence mUst starT With A capital letter.")
"A sentence must start with a capital letter."
```
