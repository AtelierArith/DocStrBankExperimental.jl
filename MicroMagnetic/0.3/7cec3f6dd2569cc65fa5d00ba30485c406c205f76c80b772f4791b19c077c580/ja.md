```
add_exch_int(sim::AbstractSim, J::Float64; k1=1, k2=-1, name="rkky")
```

インターレイヤー用のRKKY型交換を追加します。RKKY型交換のエネルギーは次のように定義されます。

$$
E_\mathrm{rkky} =  - \int_\Gamma J_\mathrm{rkky} \mathbf{m}_{i} \cdot \mathbf{m}_{j} dA
$$

ここで、$\Gamma$は磁化$\mathbf{m}_{i}$と$\mathbf{m}_{j}$を持つ二つの層の間の界面であり、$J_\mathrm{rkky}$はスペーサ層の厚さに関連する結合定数です。

有効場は次のように与えられます。

$$
\mathbf{H}_i = \frac{1}{\mu_0 M_s}  \frac{J_\mathrm{rkky}}{\Delta_z} \mathbf{m}_{j} 
$$
