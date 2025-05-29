```
hasfixedsparsity(::Type{A})::Bool
```

型 `A` のスパースパターンが変更される可能性がある場合は真です。たとえば、`Diagonal` 型はスパースパターンを変更できない場合があります。
