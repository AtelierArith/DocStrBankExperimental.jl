```
newick(tree::Tree; internal_labels=true, write_root=true)
```

`tree`に対応するNewick文字列を返します。`internal_labels == false`の場合、文字列に内部ノードのラベルを書きません。`!write_root`の場合、根ノードのラベルと時間を書きません（無根の木）。
