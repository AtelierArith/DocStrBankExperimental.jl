```
megaevolve(poke::Pokemon, mega::Union{Bool, Char} = true) → megapoke
```

`poke`のメガ進化である新しい`Pokemon`オブジェクトを作成します。`mega`が`true`の場合、デフォルトのメガ進化が使用されます。`mega`が`Char`の場合、その名前のメガ進化が使用されます。`mega`が`false`の場合、通常の形が返されます。
