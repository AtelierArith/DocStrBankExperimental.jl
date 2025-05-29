```
DiscreteFourierFeature(in_dims::Int, out_dims::Int, N::Int, period::Real)
```

The discrete Fourier filter proposed in [lindell2021bacon](@cite). For a periodic function with period $P$, the Fourier series in amplitude-phase form is

$$
s_N(x)=\frac{a_0}{2}+\sum_{n=1}^N{a_n}\cdot \sin \left( \frac{2\pi}{P}nx+\varphi _n \right)
$$

The output is guaranteed to be periodic.

## Arguments

  * `in_dims`: Number of the input dimensions.
  * `out_dims`: Number of the output dimensions.
  * `N`: $N$ in the formula.
  * `period`: $P$ in the formula.
