```
mpo = makeqMPO(Qlabels,mpo)
```

密なハミルトニアンに基づいて量子数MPOを生成します `Qlabels`

# 引数:

  * `mpo::MPO`: 密なMPO
  * `Qlabels::Array{Qnum,1}`: 物理インデックスのための量子数（均一）
