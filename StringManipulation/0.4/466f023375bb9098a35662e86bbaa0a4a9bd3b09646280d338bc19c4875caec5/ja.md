```
printable_textwidth(str::AbstractString) -> Int
```

`str`のテキスト幅を返します。これは、装飾に関連するすべてのANSIエスケープシーケンスを削除し、印刷可能な文字のみを考慮します。

!!! note
    `\n`や`\t`のような文字は通常の文字として扱われます。

