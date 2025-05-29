```
phase(N::Int, ϕ0::Real=0)
```

Single-mode Pegg-Barnett phase operator with Hilbert space cutoff $N$ and the reference phase $\phi_0$.

This operator is defined as

$$
\hat{\phi} = \sum_{m=0}^{N-1} \phi_m |\phi_m\rangle \langle\phi_m|,
$$

where

$$
\phi_m = \phi_0 + \frac{2m\pi}{N},
$$

and

$$
|\phi_m\rangle = \frac{1}{\sqrt{N}} \sum_{n=0}^{N-1} \exp(i n \phi_m) |n\rangle.
$$

# Reference

  * [Michael Martin Nieto, QUANTUM PHASE AND QUANTUM PHASE OPERATORS: Some Physics and Some History, arXiv:hep-th/9304036](https://arxiv.org/abs/hep-th/9304036), Equation (30-32).
