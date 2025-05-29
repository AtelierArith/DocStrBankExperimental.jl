```
j1_j2_model([elt::Type{T}, symm::Type{S},] lattice::InfiniteSquare;
            J1=1.0, J2=1.0, spin=1//2, sublattice=true)
```

正方格子 $J_1\text{-}J_2$ モデルは、ハミルトニアンによって定義されます

$$
H = J_1 \sum_{\langle i,j \rangle} \vec{S}_i \cdot \vec{S}_j
+ J_2 \sum_{\langle\langle i,j \rangle\rangle} \vec{S}_i \cdot \vec{S}_j,
$$

ここで $\vec{S}_i = (S_i^x, S_i^y, S_i^z)$ です。最近接および次最近接の隣接項はそれぞれ $\langle i,j \rangle$ および $\langle\langle i,j \rangle\rangle$ を使用して示します。`sublattice` キーワード引数は、ユニタリサブ格子回転を介して単一サイトユニットセル基底状態を有効にします。
