```
dual_ranking(p::Poset, compact::Bool = true)::Dict{Int,Int}
```

`Posets`の`ranking`の変種で、`p`とその双対の両方で`ranking`を組み合わせています。

`compact`が`true`に設定されている場合、レベルは0, 1, 2, 3などの番号に「圧縮」されます。そうでない場合、番号にギャップが生じる可能性があり、0から始まらないことがあります。
