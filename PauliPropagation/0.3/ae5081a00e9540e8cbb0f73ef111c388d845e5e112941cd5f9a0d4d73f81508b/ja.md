```
symboltoint(nqubits::Integer, paulis::Vector{Symbol}, qinds::Vector{Int})
```

インデックス `qinds` に作用するシンボルのベクトル `pstr` を整数パウリ文字列にマップします。他のサイトは単位行列に設定されます。`qinds` は任意の反復可能なものにすることができます。
