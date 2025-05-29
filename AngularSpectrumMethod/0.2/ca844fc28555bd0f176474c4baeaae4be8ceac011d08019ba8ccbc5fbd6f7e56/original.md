```
ScalableASM(u, λ, Δx, Δy, z; expand=true)
```

return automatically scaled diffraction field by the scalable ASM (see Ref. 1). The sampling pitch in the destination plane $\Delta_{d}$ is $\Delta_{d}=\dfrac{\lambda z}{pN\Delta_{s}}$, where $\Delta_{s}$ is the sampling pitch in the source plane, $N$ is the number of pixels in the source or destination plane, and $p=2$ is the padding factor.

> 1. [Rainer Heintzmann, Lars Loetgering, and Felix Wechsler, "Scalable angular spectrum propagation," Optica **10**, 1407-1416 (2023)](https://doi.org/10.1364/OPTICA.497809)

