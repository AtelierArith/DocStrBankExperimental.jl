```
TMSol{N,T,V1,V2,M}
```

Structure containing the solution of a validated integration.

# Fields

```
`time :: AbstractVector{T}`  Vector containing the expansion time of the `TaylorModel1` solutions

`fp   :: AbstractVector{IntervalBox{N,T}}`  IntervalBox vector representing the flowpipe

`xTMv :: AbstractMatrix{TaylorModel1{TaylorN{T},T}}`  Matrix whose entry `xTMv[i,t]` represents
the `TaylorModel1` of the i-th dependent variable, obtained at time time[t].
```
