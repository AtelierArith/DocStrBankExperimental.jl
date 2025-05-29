```
str_equal(string::String, pattern::Union{String, Regex})
```

文字列がパターンと正確に等しいか、または正規表現の場合、パターンが文字列全体に一致するかを確認します。

# 引数

  * `string`: チェックする文字列。
  * `pattern`: 比較対象のパターン。プレーンな文字列またはRegexであることができます。

文字列がパターン（プレーンな文字列の場合）と等しい場合、またはパターンが文字列全体に一致する場合（Regexの場合）にtrueを返します。それ以外の場合はfalseを返します。

# 例

```jldoctest
julia> str_equal("hello", "hello")
true
```
