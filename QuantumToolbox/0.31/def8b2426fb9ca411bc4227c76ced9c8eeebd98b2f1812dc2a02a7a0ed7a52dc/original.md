```
qft(dimensions)
```

Generates a discrete Fourier transform matrix $\hat{F}_N$ for [Quantum Fourier Transform (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform) with given argument `dimensions`.

The `dimensions` can be either the following types:

  * `dimensions::Int`: Number of basis states in the Hilbert space.
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: list of dimensions representing the each number of basis in the subsystems.

$N$ represents the total dimension, and therefore the matrix is defined as

$$
\hat{F}_N = \frac{1}{\sqrt{N}}\begin{bmatrix}
1 & 1 & 1 & 1 & \cdots & 1\\
1 & \omega & \omega^2 & \omega^3 & \cdots & \omega^{N-1}\\
1 & \omega^2 & \omega^4 & \omega^6 & \cdots & \omega^{2(N-1)}\\
1 & \omega^3 & \omega^6 & \omega^9 & \cdots & \omega^{3(N-1)}\\
\vdots & \vdots & \vdots & \vdots & \ddots & \vdots\\
1 & \omega^{N-1} & \omega^{2(N-1)} & \omega^{3(N-1)} & \cdots & \omega^{(N-1)(N-1)}
\end{bmatrix},
$$

where $\omega = \exp(\frac{2 \pi i}{N})$.

!!! warning "Beware of type-stability!"
    It is highly recommended to use `qft(dimensions)` with `dimensions` as `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) to keep type stability. See the [related Section](@ref doc:Type-Stability) about type stability for more details.

