```
RegexDict(::Tuple{Union{Regex, String}, T}...)
```

正規表現をキーとして使用し、キーを検索する際にそれらに対してテストを行う辞書を作成します。シンボルは、その名前を使用することで検索キーとして使用できます。複数の正規表現がキーに一致する場合、それらのいずれかに関連付けられた値が返される可能性があります。
