```
StretchedExponential <: InformationMeasure
StretchedExponential(; η = 2.0, base = 2)
```

The stretched exponential, or Anteneodo-Plastino, entropy [Anteneodo1999](@cite), used with [`information`](@ref) to compute

$$
S_{\eta}(p) = \sum_{i = 1}^N
\Gamma \left( \dfrac{\eta + 1}{\eta}, - \log_{base}(p_i) \right) -
p_i \Gamma \left( \dfrac{\eta + 1}{\eta} \right),
$$

where $\eta \geq 0$, $\Gamma(\cdot, \cdot)$ is the upper incomplete Gamma function, and $\Gamma(\cdot) = \Gamma(\cdot, 0)$ is the Gamma function. Reduces to [`Shannon`](@ref) entropy for `η = 1.0`.

The maximum entropy for `StrechedExponential` is a rather complicated expression involving incomplete Gamma functions (see source code).
