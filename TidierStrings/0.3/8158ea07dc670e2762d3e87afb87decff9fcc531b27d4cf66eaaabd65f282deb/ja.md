```
str_to_lower(s::AbstractString)
```

文字列内のすべての文字を小文字に変換します。

引数

  * `s`: 入力文字列。

すべての文字が小文字に変換された文字列を返します。例

```jldoctest
julia> str_to_lower("Hello World!")
"hello world!"
```
