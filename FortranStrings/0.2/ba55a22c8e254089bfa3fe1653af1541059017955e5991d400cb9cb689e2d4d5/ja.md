```
INDEX(STRING, SUBSTRING, BACK=false)
```

文字列 `STRING` の中で、部分文字列 `SUBSTRING` の最初の出現の開始位置を1から数えて返します。

`SUBSTRING` が `STRING` に存在しない場合は、0が返されます。`BACK` 引数が存在し、trueの場合、返される値は最初の出現ではなく、最後の出現の開始位置になります。
