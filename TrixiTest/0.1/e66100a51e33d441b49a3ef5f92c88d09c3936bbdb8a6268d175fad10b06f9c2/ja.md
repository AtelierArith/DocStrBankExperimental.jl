```
@trixi_test_nowarn expr [additional_ignore_content]
```

`@test_nowarn expr` の修正版で、`stderr` の内容が空でない場合にその内容を出力し、いくつかの一般的な情報文を無視します。無視すべき追加のパターンは、文字列または正規表現のリストとして渡すことができます。
