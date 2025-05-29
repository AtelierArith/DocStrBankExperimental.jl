```
PTBLM(; split=:train, dir=nothing)
PTBLM(split; [dir])
```

PTBLMデータセットは、言語モデル用のPenn Treebank文で構成されており、https://github.com/tomsercu/lstm から入手可能です。未知の単語は<unk>で置き換えられ、総語彙サイズは10000になります。
