```
is_partially_acceptable(instance::CombinatorialInstance{T}, arms::Vector{T})
```

与えられた組合せインスタンスに対して、アームのセットが解であるか、または解の部分集合でありプレイ可能であるかを返します。場合によっては、解の部分集合は解ではありません。この二つの状態の違いは、`is_feasible`を呼び出すことで明らかになります。

通常、`is_partially_acceptable`は空のアームのセットに対して`true`を返します：たとえこれが受け入れ可能な解でなくても、空のセットに要素を追加することで完全に受け入れ可能な解が得られるかもしれません。
