```
is_maximal_integral(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, AbstractLat
```

与えられた格子 `L` と `L` の固定環 $\mathcal O_K$ の素イデアル `p` に対して、`L` の `p` における完備化が整数ノルムを持ち、かつ `L` がこの性質を満たす適切なオーバー格子を持たないかどうかを返します。

もし `L` のノルムが `p` において整数でない場合、第二の出力はデフォルトで `L` になります。そうでない場合、`L` は `p` において最大であり、第二の出力は `L` であるか、または第二の出力が `L` の周囲空間にある格子 `M` であり、その `p` における完備化が整数ノルムを持つ $L_p$ の最小オーバー格子です。
