```
BSplineKernel <: AbstractKernel
BSplineKernel()
```

Represents a B-spline spreading kernel.

The order $n$ of the B-spline is directly related to the kernel half-width $M$ by $n = 2M$ (the polynomial degree is $n - 1$).

# Definition

A B-spline of order $n$ may be defined via its Fourier transform:

$$
ϕ̂(k) = Δx \operatorname{sinc}^n \left( \frac{k Δx}{2} \right)
$$

where $Δx$ is the spacing of the oversampled grid and $\operatorname{sinc}$ is the [unnormalised sinc function](https://en.wikipedia.org/wiki/Sinc_function).

# Implementation details

In the implementation, this kernel is evaluated using [de Boor's algorithm](https://en.wikipedia.org/wiki/De_Boor%27s_algorithm).
