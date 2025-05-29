c = split(s::SeisCon, inds)

`s`の`blocks[inds]`を参照することで、新しいSeisConオブジェクト`c`をコピーせずに作成します。

`inds`はインデックスの配列、範囲、またはスカラーであることができます。

# 例

```julia-repl
julia> b = split(s, 1:10);
julia> c = split(b, [1; 7; 9]);
julia> d = split(c, 1);
```

そして、`d`と`s`がメモリ内の同じ場所を参照していることを確認できます。

```julia-repl
julia> s.blocks[1] === d.blocks[1]
true
```
