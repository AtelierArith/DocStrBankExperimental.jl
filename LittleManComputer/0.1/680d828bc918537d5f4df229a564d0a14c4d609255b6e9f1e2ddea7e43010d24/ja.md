```
symboltable(lines::AbstractArray{<:AbstractString})
```

コードで使用されるラベルのアドレスをシンボルテーブルに記録します。これを辞書として返します。

```
symtable = symboltable("foobar.lmc")

# LOOPラベルのアドレスを取得
address = symtable["LOOP"]
```
