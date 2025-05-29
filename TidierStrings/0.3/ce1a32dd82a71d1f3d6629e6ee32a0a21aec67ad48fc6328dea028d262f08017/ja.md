```
str_squish(string::String)
```

文字列を圧縮し、連続する空白を単一の空白に置き換え、先頭および末尾の空白を削除します。

# 引数 `string`: 圧縮する文字列。 戻り値 圧縮された文字列のバージョン。

# 例

```jldoctest
julia> str_squish("  This    is a string   with   spaces   ")
"This is a string with spaces"

julia> str_squish("  Leading and trailing spaces   ")
"Leading and trailing spaces"
```
