c = split_con(s::SeisCon, inds)

新しい SeisCon オブジェクト `c` を作成しますが、`s.blocks[inds]` を参照することでコピーは行いません。

`inds` はインデックスの配列、範囲、またはスカラーであることができます。

# 例

```julia-repl
julia> b = split_con(s, 1:10);
julia> c = split_con(b, [1; 7; 9]);
julia> d = split_con(c, 1);
```

そして、`d` と `s` がメモリ内の同じ場所を参照していることを確認できます。

```julia-repl
julia> s.blocks[1] === d.blocks[1]
true
```
