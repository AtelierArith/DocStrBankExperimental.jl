```
add_dmi_int(sim::MicroSimGPU, D::Tuple{Real, Real, Real}; k1=1, k2=-1, name="dmi_int")
```

Add an interlayer DMI to the system. The energy of interlayer DMI is defined as 

$$
E_\mathrm{dmi-int} =  \int_\Gamma \mathbf{D} \cdot \left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right) dA
$$

where $\Gamma$ is the interface between two layers with magnetizations $\mathbf{m}_{i}$ and $\mathbf{m}_{j}$.  $\mathbf{D}$ is the effective DMI vector. 

The effective field is given

$$
\mathbf{H}_i = \frac{1}{\mu_0 M_s \Delta_z}  \mathbf{D} \times \mathbf{m}_{j} 
$$
