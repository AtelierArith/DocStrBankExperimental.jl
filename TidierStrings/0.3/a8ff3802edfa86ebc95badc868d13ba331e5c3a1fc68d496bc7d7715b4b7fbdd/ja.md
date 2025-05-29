```
str_like(string, pattern::String; ignore_case::Bool = true)
```

SQLのようなパターンマッチングを使用して、入力ベクターの各文字列にパターンを検出します。

引数

  * `string`: 入力文字列。
  * `pattern`: チェックするパターン。文字列または正規表現である可能性があります。
  * `ignore_case`: マッチング時に大文字と小文字を無視するかどうか。デフォルトは`true`です。

戻り値 パターンに文字列が一致するかどうかを示すブール値のベクター。

```jldoctest
julia> str_like("hello", "h_llo")
true

julia> str_like.(["Hello", "world", "HELLO", "WORLD"], "H_llo")
4-element BitVector:
 1
 0
 1
 0
```
