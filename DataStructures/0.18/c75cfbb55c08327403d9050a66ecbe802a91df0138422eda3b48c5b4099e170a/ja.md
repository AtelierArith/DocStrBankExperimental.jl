```
in(p, sc)
```

`p`が`sc`に含まれている場合はtrueを返します。`sc`がSortedDictまたはSortedMultiDictの場合、`p`はkey=>valueペアです。`sc`がSortedSetの場合、`p`はキーである必要があります。時間: O(*c* log *n* + *d*)はSortedDictおよびSortedSetの場合で、*d*は2つの値を比較するための時間を表します。SortedMultiDictの場合、時間はO(*c* log *n* + *dl*)で、*l*は与えられたペアのキーを持つエントリの数を表します。（したがって、この呼び出しは同じキーが多数の値に対応する場合には非効率的であり、代替手段を検討する必要があります。）
