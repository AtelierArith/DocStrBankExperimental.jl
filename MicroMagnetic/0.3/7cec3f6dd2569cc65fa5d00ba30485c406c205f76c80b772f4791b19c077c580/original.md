```
add_exch_int(sim::AbstractSim, J::Float64; k1=1, k2=-1, name="rkky")
```

Add an RKKY-type exchange for interlayers. The energy of RKKY-type exchange is defined as 

$$
E_\mathrm{rkky} =  - \int_\Gamma J_\mathrm{rkky} \mathbf{m}_{i} \cdot \mathbf{m}_{j} dA
$$

where $\Gamma$ is the interface between two layers with magnetizations $\mathbf{m}_{i}$ and $\mathbf{m}_{j}$, $J_\mathrm{rkky}$ is the coupling constant which is related to the spacer layer thickness. 

The effective field is given then as

$$
\mathbf{H}_i = \frac{1}{\mu_0 M_s}  \frac{J_\mathrm{rkky}}{\Delta_z} \mathbf{m}_{j} 
$$
