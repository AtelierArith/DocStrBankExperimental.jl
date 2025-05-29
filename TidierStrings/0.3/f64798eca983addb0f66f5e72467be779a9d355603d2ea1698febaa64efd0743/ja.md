```
str_to_title(s::AbstractString)
```

文字列内の各単語の最初の文字を大文字に変換します。

引数

  * `s`: 入力文字列。

戻り値 各単語の最初の文字が大文字に変換された文字列。

例

```jldoctest
julia> str_to_title("hello world!")
"Hello World!"

julia> str_to_title("This is a title")
"This Is A Title"
```
