```
mpo = makeqMPO(Qlabels,mpo)
```

密なハミルトニアンに基づいて量子数MPOを生成します `Qlabels`

# 引数:

  * `mpo::MPO`: 密なMPO
  * `Qlabels::Array{Array{Qnum,1},1}`: 物理インデックスの量子数（ベクトルのサイズの剰余）
