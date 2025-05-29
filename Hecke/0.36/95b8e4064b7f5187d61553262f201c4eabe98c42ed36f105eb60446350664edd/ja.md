```
hermitian_local_genera(E::NumField, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, rank::Int,
                       det_val::Int, min_scale::Int, max_scale::Int)
                                                  -> Vector{HermLocalGenus}
```

代数 `E` のエルミート格子に対するすべての局所属の記号を返します。基底体 $K$ において、$\mathcal O_K$ の素イデアル `p` に対して、それぞれの局所属は `rank` に等しいランクを持ち、スケール $\mathfrak P$-評価が `min_scale` と `max_scale` の間に制限され、行列式の `p`-評価が `det_val` に等しいです。ここで、$\mathfrak P$ は `p` の上にある $\mathcal O_E$ の素イデアルです。
