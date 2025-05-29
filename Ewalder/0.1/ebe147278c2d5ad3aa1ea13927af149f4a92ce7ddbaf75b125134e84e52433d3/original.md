```
System(; latvecs::Vector{NTuple{3, Float}},
         pos::Vector{Vec3}
         c0::Float64 = 6.0
         c1::Float64 = 2.0)
```

Create a system that is periodic in each of the three supercell lattice vectors `latvecs` and with atom positions `pos`. The optional parameter `c0` controls accuracy of Ewald summation. The default is `c0 = 6`, which yields errors of order `1e-12` (smaller `c0` will run faster). The optional parameter `c1` controls the balance between real and Fourier space summation (larger `c1` implies more real-space summation).
