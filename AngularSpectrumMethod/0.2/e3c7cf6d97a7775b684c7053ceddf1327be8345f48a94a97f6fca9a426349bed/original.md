```
TiltedASM(u, λ, Δx, Δy, T; expand=true, weight=false)
```

return tilted diffraction field for a rotation matrix $T$ by the tilted ASM (see Ref. 1, 2). If `weight=true`, a diagonal weighting matrix is used as the Jacobian determinant (default `false`). In this case, the energy conservation improves, but the computational cost is high (see Ref. 3).

!!! note
    [Rotations.jl](https://github.com/JuliaGeometry/Rotations.jl) is helpful in generating rotation matrices.


> 1. [Kyoji Matsushima, Hagen Schimmel, and Frank Wyrowski, "Fast calculation method for optical diffraction on tilted planes by use of the angular spectrum of plane waves," J. Opt. Soc. Am. A **20**, 1755-1762 (2003)](https://doi.org/10.1364/JOSAA.20.001755)
> 2. [Kyoji Matsushima, "Formulation of the rotational transformation of wave fields and their application to digital holography," Appl. Opt. **47**, D110-D116 (2008)](https://doi.org/10.1364/AO.47.00D110)
> 3. [James G. Pipe and Padmanabhan Menon, "Sampling density compensation in MRI: Rationale and an iterative numerical solution," Magn. Reson. Med. **41**, 179-186 (1999)](https://doi.org/10.1002/(sici)1522-2594(199901)41:1%3C179::aid-mrm25%3E3.0.co;2-v)

