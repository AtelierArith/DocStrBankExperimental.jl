```
norm(a::AlgAssRelOrdIdl{S, T, U}, O::AlgAssRelOrd{S, T, U}; copy::Bool = true)
  where { S, T, U } -> T
```

$$
O
$$

の（おそらく分数の）イデアルとして考えられる$a$のノルムを返します。
