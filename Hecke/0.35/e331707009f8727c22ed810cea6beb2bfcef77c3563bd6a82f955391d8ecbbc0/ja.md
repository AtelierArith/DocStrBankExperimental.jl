```
getindex(x::FinGenAbGroupElem, v::AbstractVector{Int}) -> Vector{ZZRingElem}
```

要素$x$の$i$-番目の成分を返します。ただし、$i \in v$です。

!!! note
    この関数は非効率的です。なぜなら、要素は内部的にZZMatrixを使用して保存されているため、この関数はベクトルを出力します。

