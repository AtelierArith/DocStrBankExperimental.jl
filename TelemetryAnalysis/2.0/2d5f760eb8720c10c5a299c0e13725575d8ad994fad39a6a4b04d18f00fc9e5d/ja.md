```
search_variables(pattern::T, database::TelemetryDatabase = get_default_database()) where T<:Union{AbstractString, Regex} -> Nothing
```

`database` に登録されている変数を検索し、そのラベル、エイリアス、または説明に `pattern` が含まれているものを探します。`pattern` は文字列または正規表現である可能性があります。

!!! note
    `pattern` が文字列の場合、検索は大文字と小文字を区別しません。


!!! note
    `database` が指定されていない場合、デフォルトのものが使用されます。

