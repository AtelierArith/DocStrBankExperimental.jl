```
combine_parallel_lines!(net::Network)
```

Combine any parallel single phase lines without loads on intermediate busses into one multiphase  line. This method is useful for making a mesh network radial when the mesh components are products of modeling single phase voltage regulators in load flow software such as OpenDSS.
