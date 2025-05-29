```
untokenise(txt::Txt, W::DLMSpace; kwargs) -> String
```

`txt.tokenised`内のトークンの部分文字列を連結して返します。

# キーワード引数

  * `restore_frozen = true` は、凍結された部分文字列が再挿入されるかどうかを制御します
  * `restore_case = true` は、元のケースが再適用されるかどうかを制御します
