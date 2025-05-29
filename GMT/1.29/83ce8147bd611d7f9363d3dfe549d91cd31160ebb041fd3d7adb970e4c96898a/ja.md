```
bissextile(year::Integer) -> Bool
```

非常に高速な関数で、年がうるう年かどうかをチェックします。詳細は https://hueffner.de/falk/blog/a-leap-year-check-in-three-instructions.html を参照してください。

年が0未満の場合は、従来の方法に戻ります。
