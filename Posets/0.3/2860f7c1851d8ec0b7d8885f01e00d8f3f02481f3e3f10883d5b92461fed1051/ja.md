```
ranking(p::Poset)::Dict{Int,Int}
```

順序集合 `p` のランキングを作成します。これは `p` の各要素に対するランキングを提供する辞書です。最小要素はランク0を持ち、最小要素の上にのみある要素はランク1を持ちます。以降同様です。
