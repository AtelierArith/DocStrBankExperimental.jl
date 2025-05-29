`conjugate(p,conjugation)`

このプログラムは、別の生成子によって生成子を共役させることによってプレゼンテーションを修正します。適用する共役は、`display_balanced`の結果と同じスタイルの長さ3の文字列で説明されます。つまり、`"abA"`は2番目の生成子を最初の生成子による共役に置き換えることを意味し、`"Aba"`はそれを最初の生成子の逆による共役に置き換えることを意味します。

```julia-rep1
julia> display_balanced(P)
1: dabcd=abcda
2: dabcdb=cabcda
3: bcdabcd=dabcdbc

julia> display_balanced(conjugate(P,"Cdc"))
<< presentation with 4 generators, 3 relators of total length 36>>
1: dcabdc=cabdca
2: abdcab=cabdca
3: bdcabd=cabdca
```
