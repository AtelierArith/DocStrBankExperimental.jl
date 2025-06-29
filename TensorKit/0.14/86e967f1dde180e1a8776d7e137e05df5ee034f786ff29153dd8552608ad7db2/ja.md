```
flip(t::AbstractTensorMap, I) -> t′::AbstractTensorMap
```

新しいテンソルを返します。これは `t` と同型ですが、インデックス `i` の矢印が `i ∈ I` を満たす場合に反転されます。すなわち、`space(t′, i) = flip(space(t, i))` です。

!!! note
    `flip` が `i ∈ I` の各インデックスに適用する同型は、`@tensor` 収縮内でその後に収縮される2つのインデックスを反転させることが、最初にそれらのインデックスを反転させずに得られるのと同じ結果をもたらすようになっています。しかし、`flip` は反転的ではありません。すなわち、一般には `flip(flip(t, I), I) != t` です。元のテンソルを取得するには、`inv` キーワードを使用できます。すなわち、`flip(flip(t, I), I; inv=true) == t` が成り立ちます。

