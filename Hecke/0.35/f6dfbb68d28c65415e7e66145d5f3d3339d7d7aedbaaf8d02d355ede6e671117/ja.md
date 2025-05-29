```
normred(a::AlgAssRelOrdIdl{S, T, U}; copy::Bool = true) where { S, T, U } -> T
```

$ a $ を `order(a)` の（おそらく分数の）イデアルとして考えたときの縮小ノルムを返します。
