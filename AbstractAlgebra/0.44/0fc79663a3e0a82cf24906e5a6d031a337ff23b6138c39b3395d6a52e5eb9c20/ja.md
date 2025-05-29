```
nullspace(M::MatElem{T}) where {T <: FieldElement}
```

行列 $M$ のヌルity $\nu$ と、$M$ の右ヌル空間の基底 $N$（列ベクトルからなる）からなるタプル $(\nu, N)$ を返します。すなわち、$MN$ がゼロ行列となるような $N$ です。$M$ が $m \times n$ 行列である場合、$N$ は $n \times \nu$ 行列になります。
