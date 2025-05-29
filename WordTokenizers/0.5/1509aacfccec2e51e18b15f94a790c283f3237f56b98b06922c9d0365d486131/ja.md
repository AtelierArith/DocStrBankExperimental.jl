```
tweet_tokenize(input::AbstractString) => tokens
```

Twitterに対応したトークナイザーで、新しいドメインやタスクに適応しやすく柔軟に設計されています。

基本的なロジックは以下の通りです：

1. 正規表現はWORD*REGEX（コアトークナイザー）、HANG*REGEX、EMOTICONS_REGEXのために作成されています。
2. HTMLエンティティ、ツイートハンドルの置換、繰り返し文字の長さの短縮、その他の機能により、ツイートに適したものになります。
3. 文字列がトークン化されて返されます。
4. `preserve_case`はデフォルトで`true`に設定されています。`false`に設定すると、トークナイザーは絵文字を除いてすべてを小文字に変換します。

例：

```
julia> tweet_tokenize("This is a cooool #dummysmiley: :-) :-P <3 and some arrows < > -> <--")

16-element Array{SubString{String},1}:
 "This"
 "is"
 "a"
 "cooool"
 "#dummysmiley"
 ":"
 ":-)"
 ":-P"
 "<3"
 "and"
 "some"
 "arrows"
 "<"
 ">"
 "->"
 "<--"
```
