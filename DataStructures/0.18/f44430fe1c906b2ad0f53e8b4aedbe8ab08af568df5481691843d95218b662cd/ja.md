```
issubset(iterable, ss)
```

この関数は、最初の引数の各アイテムがSortedSet `ss`の要素であるかどうかをチェックします。エントリは`ss`のキータイプに変換可能でなければなりません。時間: O(*cm* log *n*), ここで *n* は `ss` のサイズ、*m* は `iterable` のアイテム数です。
