```
ModifiedHypernettedChain <: Closure
```

Implements the Modified Hypernetted Chain closure $b(r) = b_{HS}(r) $. Here $b_{HS}(r/σ)=\left((a_1+a_2x)(x-a_3)(x-a_4)/(a_3 a_4)\right)^2$ for $x<a_4$ and $b_{HS}(r)=\left(A_1 \exp(-a_5(x-a_4))\sin(A_2(x-a_4))/r\right)^2$ is the hard sphere bridge function found in Malijevský & Labík. The parameters are defined as

$$
x = r/σ-1
$$

$$
A_1 = (a_1+a_2 a_4)(a_4-a_3)(a_4+1)/(A_2 a_3 a_4)
$$

$$
A_2 =  \pi / (a_6 - a_4 - 1)
$$

$$
a_1 = \eta (1.55707 - 1.85633\eta) / (1-\eta)^2
$$

$$
a_2 = \eta (1.28127 - 1.82134\eta) / (1-\eta)
$$

$$
a_3 =  (0.74480 - 0.93453\eta)
$$

$$
a_4 = (1.17102 - 0.68230\eta)
$$

$$
a_5 = 0.15975/\eta^2
$$

$$
a_6 = (2.69757 - 0.86987\eta)
$$

and $\eta$ is the volume fraction of the hard sphere reference system. This closure only works for single component systems in three dimensions. By default, $\sigma = 1.0$.

Example:

```julia
closure = ModifiedHypernettedChain(0.4)
closure = ModifiedHypernettedChain(0.4; sigma=0.8)
```

References:

Lado, F. "Perturbation correction for the free energy and structure of simple fluids." Physical Review A 8.5 (1973): 2548.

Malijevský, Anatol, and Stanislav Labík. "The bridge function for hard spheres." Molecular Physics 60.3 (1987): 663-669.
