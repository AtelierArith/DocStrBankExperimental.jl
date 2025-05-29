```
get_user_option(text::String, options::AbstractVector) -> Int
```

ユーザーオプションを取得します。`text`はユーザーに表示される情報で、`options`はオプションのベクターです。この関数は、`options`に対する選択インデックスを返します。ユーザーがオプションを選択しなかった場合は-1を返します。
