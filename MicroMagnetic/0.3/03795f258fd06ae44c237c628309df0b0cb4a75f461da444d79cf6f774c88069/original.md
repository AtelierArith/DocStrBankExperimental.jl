```
add_hex_anis(sim::AbstractSim; K1=0, K2=0, K3=0, name="hex")
```

Add hexagonal anisotropy to a simulation. The energy density of the anisotropy is defined as:

$$
E = K_1 \sin^2 \theta + K_2 \sin^4 \theta + K_3 \sin^6 \theta \cos 6\phi
$$

# Example

```julia
add_hex_anis(sim, K1=1e3, K2=0, K3=1e2)
```
