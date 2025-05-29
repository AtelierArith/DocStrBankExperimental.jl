```
is_maximal(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, AbstractLat
```

与えられた格子 `L` と、`L` の固定環 $\mathcal O_K$ における素イデアル `p` があり、$L_p$ のノルムが整数である場合、`L` が `p` において最大整数であるかどうかを返します。

もし `L` が `p` において局所的に最大であるなら、第二の出力は `L` になります。そうでない場合は、`L` の同じ環境空間にある格子 `M` であり、`p` における完備化が整数ノルムを持ち、$L_p$ の適切なオーバー格子です。
