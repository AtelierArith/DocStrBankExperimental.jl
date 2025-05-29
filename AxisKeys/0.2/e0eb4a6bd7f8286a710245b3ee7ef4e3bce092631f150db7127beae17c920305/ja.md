```
rekey(A, (1:10, [:a, :b]))
rekey(A, 2 => [:a, :b])
rekey(A, :y => [:a, :b])
```

`Tuple`や`Pair`を介してKeyedArrayのキーを再設定します。`dim => newkey`。もし`A`が名前付き次元を持っている場合は、`dimname => newkey`も渡すことができます。
