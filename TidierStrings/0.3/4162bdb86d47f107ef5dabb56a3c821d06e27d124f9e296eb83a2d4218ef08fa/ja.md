```
str_subset(string::String, pattern::Union{String, Regex})
```

パターンの存在に基づいて文字列のサブセットを取得します。パターンが文字列内に存在する場合、関数は元の文字列を返します。パターンが文字列内に見つからない場合、関数は空の文字列を返します。

# 引数

  * `string`: サブセットを抽出する文字列。
  * `pattern`: 文字列内で検索するパターン。プレーンな文字列またはRegexである可能性があります。

パターンが見つかった場合は元の文字列を返し、そうでない場合は空の文字列を返します。

# 例

```jldoctest
julia> str_subset("Hello world!", "world")
"Hello world!"

julia> str_subset("Hello world!", "universe")
""
```
