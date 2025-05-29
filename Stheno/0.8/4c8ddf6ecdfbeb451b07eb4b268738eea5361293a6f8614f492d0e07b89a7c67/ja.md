```
additive_gp(fs, indices)
```

`fs` は GP のコレクションであり、`indices` は整数インデックスのコレクションのコレクションです。例えば、`indices` は `[1:2, 3, 4:6]` のようなもので、その場合 `fs` は正確に三つの要素を含む必要があります。一般に、この関数は `length(fs) == length(indices)` を要求します。

次のように与えられる GP を生成します。

```julia
sum(fs[1](x[indices[1]]) + fs[2](x[indices[2]]) + ... + fs[D](x[indices[D]]))
```
