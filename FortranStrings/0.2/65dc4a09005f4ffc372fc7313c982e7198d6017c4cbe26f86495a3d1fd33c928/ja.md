```
SCAN(STRING, CHARSET, BACK=false)
```

文字列 `STRING` 内の文字セット `CHARSET` の最初の出現の開始位置を1から数えて返します。

`CHARSET` が `STRING` に存在しない場合、0が返されます。`BACK` 引数が存在し、true の場合、返される値は最初の出現ではなく最後の出現の開始位置になります。
