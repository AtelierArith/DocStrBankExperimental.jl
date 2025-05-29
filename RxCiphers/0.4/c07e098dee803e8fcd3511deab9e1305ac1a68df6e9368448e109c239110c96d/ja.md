```
untokenise(txt::Txt, W::NCharSpace; kwargs) -> String
```

`txt.tokenised`のトークンに対する部分文字列の連結を返します。

# キーワード引数

  * `restore_frozen = true` は、凍結された部分文字列が再挿入されるかどうかを制御します
  * `restore_case = true` は、元のケースが再適用されるかどうかを制御します
