```
PTBLM(; split=:train, dir=nothing)
PTBLM(split; [dir])
```

The PTBLM dataset consists of Penn Treebank sentences for language modeling, available from https://github.com/tomsercu/lstm. The unknown words are replaced with <unk> so that the total vocabulary size becomes 10000.
