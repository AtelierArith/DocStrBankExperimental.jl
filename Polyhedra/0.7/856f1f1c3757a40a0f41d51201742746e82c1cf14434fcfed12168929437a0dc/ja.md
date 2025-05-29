```
vrep(V::AbstractMatrix, R::AbstractMatrix, Rlinset::BitSet=BitSet())
```

点 $V_i$ によって定義される多面体の V 表現を作成します。`i in Rlinset` の場合は線 $R_i$、それ以外の場合は光線 $R_i$ です。ここで、$V_i$（それぞれ $R_i$）は `V`（それぞれ `R`）の $i$ 行目、すなわち `V[i,:]`（それぞれ `R[i,:]`）です。
