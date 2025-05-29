```
normred(a::AlgAssRelOrdIdl{S, T}, O::AlgAssRelOrd{S, T}; copy::Bool = true)
  where { S, T, U } -> T
```

$$
O
$$

の（おそらく分数の）イデアルとして考えたときの$a$の縮小ノルムを返します。$a$を含む代数は単純で中心的であると仮定します。
