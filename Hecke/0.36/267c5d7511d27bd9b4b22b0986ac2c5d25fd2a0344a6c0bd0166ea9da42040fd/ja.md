```
pseudo_basis(O::AlgAssRelOrd; copy::Bool = true)
```

$$
O
$$

の擬似基底を返します。すなわち、$O = \bigoplus_i a_i e_i$となるペア$(e_i, a_i)$のベクトル$v$を返します。ここで、$e_i$は`algebra(O)`の要素であり、$a_i$は`base_ring(O)`の分数イデアルです。
