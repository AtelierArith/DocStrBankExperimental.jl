```
is_subfield(K::KummerExt, L::KummerExt) -> Bool, Vector{Tuple{AbsSimpleNumFieldElem, Vector{Int}}}
```

基底体 $k$ の二つのクンマ拡張が与えられたとき、$K$ が $L$ の部分体であれば真と、$K$ から $L$ への注入を定義するためのデータを返します。そうでなければ、関数は偽といくつかの無意味なデータを返します。
