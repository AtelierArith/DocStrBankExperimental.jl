```
add_dmi_int(sim::MicroSimGPU, D::Tuple{Real, Real, Real}; k1=1, k2=-1, name="dmi_int")
```

システムに層間DMIを追加します。層間DMIのエネルギーは次のように定義されます。

$$
E_\mathrm{dmi-int} =  \int_\Gamma \mathbf{D} \cdot \left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right) dA
$$

ここで、$\Gamma$は磁化$\mathbf{m}_{i}$と$\mathbf{m}_{j}$を持つ二つの層の間の界面です。$\mathbf{D}$は有効DMIベクトルです。

有効場は次のように与えられます。

$$
\mathbf{H}_i = \frac{1}{\mu_0 M_s \Delta_z}  \mathbf{D} \times \mathbf{m}_{j} 
$$
