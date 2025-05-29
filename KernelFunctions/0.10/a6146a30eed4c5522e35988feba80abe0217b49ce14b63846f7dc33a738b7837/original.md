```
MaternKernel(; ν::Real=1.5, metric=Euclidean())
```

Matérn kernel of order `ν` with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the Matérn kernel of order $\nu > 0$ is defined as

$$
k(x,x';\nu) = \frac{2^{1-\nu}}{\Gamma(\nu)}\big(\sqrt{2\nu} d(x, x')\big) K_\nu\big(\sqrt{2\nu} d(x, x')\big),
$$

where $\Gamma$ is the Gamma function and $K_{\nu}$ is the modified Bessel function of the second kind of order $\nu$. By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

A Gaussian process with a Matérn kernel is $\lceil \nu \rceil - 1$-times differentiable in the mean-square sense.

!!! note
    Differentiation with respect to the order ν is not currently supported.


See also: [`Matern12Kernel`](@ref), [`Matern32Kernel`](@ref), [`Matern52Kernel`](@ref)
