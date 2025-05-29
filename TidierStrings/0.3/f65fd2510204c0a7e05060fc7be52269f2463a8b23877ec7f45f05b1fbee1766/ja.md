```
str_count(string::String, pattern::Union{String, Regex})
```

文字列内のパターンの重複しない出現回数をカウントします。

# 引数

  * `string`: パターンをカウントする文字列。
  * `pattern`: 文字列内で見つけるための文字列または正規表現。

パターンには特別なロジックを含めることができます：

| を使用して「または」を表現します（例："red|blue"は「red」または「blue」を含む任意の文字列をカウントします）。 戻り値は、文字列内のパターンの重複しない出現回数です。 例

```jldoctest
julia> str_count("The blue sky is blue", "blue")
2

julia> str_count("The blue sky is blue", r"blu")
2

julia> str_count("The blue sky is blue", "blue|sky")
3
```
