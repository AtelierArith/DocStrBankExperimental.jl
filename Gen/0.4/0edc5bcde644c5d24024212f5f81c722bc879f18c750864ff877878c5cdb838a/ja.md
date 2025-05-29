```
(choices1, choices2) = unpair(choices::ChoiceMap, key1::Symbol, key2::Symbol)
```

`key1` と `key2` における2つのサブアサインメントを返します。どちらか一方または両方が空である可能性があります。

`key1` と `key2` 以外のキーにトップレベルの値や非空のトップレベルサブアサインメントがある場合はエラーです。
