```
TMSol{N,T,V1,V2,M}
```

検証された積分の解を含む構造体。

# フィールド

```
`time :: AbstractVector{T}`  `TaylorModel1` ソリューションの展開時間を含むベクトル

`fp   :: AbstractVector{IntervalBox{N,T}}`  フローペイプを表す IntervalBox ベクトル

`xTMv :: AbstractMatrix{TaylorModel1{TaylorN{T},T}}`  エントリ `xTMv[i,t]` が時間 time[t] で得られた i 番目の従属変数の `TaylorModel1` を表す行列。
```
