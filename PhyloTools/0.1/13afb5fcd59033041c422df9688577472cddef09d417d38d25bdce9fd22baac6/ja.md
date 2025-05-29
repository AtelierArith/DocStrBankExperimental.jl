```
readnw(s::AbstractString, I::Type)
```

Newick文字列を木に読み込みます。元のNewick標準をサポートしています (http://evolution.genetics.washington.edu/phylip/newicktree.html)。内部ノードのサポート値またはノードラベルのいずれかを持つことができますが、両方を持つことはできません。
