```
hrep(A::AbstractMatrix, b::AbstractVector, linset::BitSet=BitSet())
```

不等式 $\langle A_i, x \rangle = b_i$ によって定義される多面体の H-表現を作成します。ここで `i in linset` の場合は、そうでない場合は $\langle A_i, x \rangle \le b_i$ です。$A_i$ は `A` の $i$ 行目、すなわち `A[i,:]` であり、$b_i$ は `b[i]` です。
