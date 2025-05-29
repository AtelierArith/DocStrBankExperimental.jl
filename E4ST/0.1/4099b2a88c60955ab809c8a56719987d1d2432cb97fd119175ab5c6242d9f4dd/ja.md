```
struct YearString end

YearString(s) -> s

YearString(n::Number) -> year2str(n)
```

これは、年の列が正しく文字列として解析されることを保証するための変換器として機能する型です。 空白が与えられた場合は、空白のままにします。
