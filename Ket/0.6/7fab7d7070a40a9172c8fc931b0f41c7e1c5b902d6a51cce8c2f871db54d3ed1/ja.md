```
state_sindici_piani_ket([T=ComplexF64], d::Integer, k::Integer = 1, l::Integer = d; coeff = inv(_sqrt(T, 2)))
```

偶数の局所次元 `d` × `d` のシンディチ・ピアニ状態のケットを生成します。

参考文献: Sindici and Piani, [arXiv:1708.06595](http://arxiv.org/abs/1708.06595)
