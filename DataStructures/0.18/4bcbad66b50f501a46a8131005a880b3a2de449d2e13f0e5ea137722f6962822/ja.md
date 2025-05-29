```
union!(ss, iterable)
```

この関数は、2番目の引数（iterableである必要があります）から各アイテムをSortedSet `ss` に挿入します。アイテムは `ss` のキータイプに変換可能でなければなりません。時間: O(*ci* log *n*) ここで *i* はiterable引数のアイテム数です。
