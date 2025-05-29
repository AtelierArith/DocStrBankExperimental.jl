```
freeze(dd::AbstractDict)
```

辞書を不変にするために、`Tuple`に基づく`LittleDict`に変換します。`Tuple`に基づく`LittleDict`は、特にキーがすべて具体的に型付けされている場合、`Vector`に基づく`LittleDict`よりも高速です。
