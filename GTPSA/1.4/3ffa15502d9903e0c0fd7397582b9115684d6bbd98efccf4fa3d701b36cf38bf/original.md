```
Descriptor(nv::Integer, mo::Integer, np::Integer, po::Integer)::Descriptor
```

Creates a TPSA `Descriptor` with `nv` variables and `np` parameters. The maximum  truncation order is `mo` (including the parameters), and the truncation order for  the parameters part of a monomial is `po`.

### Input

  * `nv` – Number of variables in the TPSA
  * `mo` – Maximum truncation order of the TPSA including variables and parameters
  * `np` – Number of parameters in the TPSA
  * `po` – Truncation order of the parameters part of a monomial
