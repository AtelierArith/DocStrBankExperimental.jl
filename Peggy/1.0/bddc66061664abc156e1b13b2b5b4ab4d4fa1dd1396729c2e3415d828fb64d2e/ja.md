```
CHAR(charclass::String)
```

単一の文字に対する正規表現文字クラスのパーサーを作成します。

`Regex("[:charclass]")`と機能的に同一ですが、空の文字列にマッチしないことが知られています。これは、不必要で高コストな左再帰のオーバーヘッドを避けるために重要です。

# 例

```jldoctet
julia> g = @grammar begin
       number = [ digit ds:(digit...)  { parse(Int, *(digit, ds...)) } ]
       digit = CHAR("[:digit:]")
       end;

julia> g("1234")
1234
```
