```
ElectronicEntropy <: InformationMeasure
ElectronicEntropy(; h = Shannon(; base = 2), j = ShannonExtropy(; base = 2))
```

The ["electronic entropy"](https://en.wikipedia.org/wiki/Electronic_entropy) measure is defined in discrete form in [Lad2015](@citet) as

$$
H_{EL}(p) = H_S(p) + J_S(P),
$$

where $H_S(p)$ is the [`Shannon`](@ref) entropy and $J_S(p)$ is the [`ShannonExtropy`](@ref) extropy of the probability vector $p$.
