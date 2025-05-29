```
pseudo_basis(a::AlgAssRelOrdIdl; copy::Bool = true)
```

$$
a
$$

の擬似基底を返します。すなわち、$a = \bigoplus_i a_i e_i$となるペア$(e_i, a_i)$のベクトル$v$を返します。ここで、$e_i$は`algebra(a)`の要素であり、$a_i$は`base_ring(left_order(a))`の分数イデアルです。
