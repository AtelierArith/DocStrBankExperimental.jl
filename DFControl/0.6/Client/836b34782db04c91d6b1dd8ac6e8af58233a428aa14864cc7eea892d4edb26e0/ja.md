```
PseudoSet(;name   ::String,
           dir    ::String,
           pseudos::Dict)
```

`dir`ディレクトリにある擬似ポテンシャルのセットを表します。`configure_pseudoset`で設定した後、`load(<server>, PseudoSet("name"))`でロードできます。
