```
jordan_decomposition(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem})
                            -> Vector{MatElem}, Vector{MatElem}, Vector{Int}
```

素イデアル `p` における格子 `L` の完備化のジョルダン分解を返します。

返される値は、同じ長さ $r$ の三つのリスト $(M_i)_i$, $(G_i)_i$ および $(s_i)_i$ から構成されます。行列 $M_i$ の行スパンの完備化は、グラム行列 $G_i$ と $p$-進評価のスケール $s_i$ を持つモジュラー部分格子 $L_i$ への $L_{p}$ のジョルダン分解をもたらします。
