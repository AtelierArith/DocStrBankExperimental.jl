```
DoubleArrayTrie(keys::AbstractVector{<:AbstractString}; bin_mode = true)
```

文字列のリストを受け取り、ダブルアレイトライを構築します。`keys`が`Vector`の場合、`sort!`と`unique!`によって変更されます。`bin_mode = true`を設定すると、非ASCII文字列に必要な`' '`を文字として許可します。
