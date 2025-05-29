```
embed(s, d, τ [, h])
```

Embed `s` using delay coordinates with embedding dimension `d` and delay time `τ` and return the result as a [`Dataset`](@ref). Optionally use weight `h`, see below.

Here `τ > 0`, use [`genembed`](@ref) for a generalized version.

## Description

If `τ` is an integer, then the $n$-th entry of the embedded space is

$$
(s(n), s(n+\tau), s(n+2\tau), \dots, s(n+(d-1)\tau))
$$

If instead `τ` is a vector of integers, so that `length(τ) == d-1`, then the $n$-th entry is

$$
(s(n), s(n+\tau[1]), s(n+\tau[2]), \dots, s(n+\tau[d-1]))
$$

The resulting set can have same invariant quantities (like e.g. lyapunov exponents) with the original system that the timeseries were recorded from, for proper `d` and `τ`. This is known as the Takens embedding theorem [^Takens1981] [^Sauer1991]. The case of different delay times allows embedding systems with many time scales, see[^Judd1998].

If provided, `h` can be weights to multiply the entries of the embedded space. If `h isa Real` then the embedding is

$$
(s(n), h \cdot s(n+\tau), w^2 \cdot s(n+2\tau), \dots,w^{d-1} \cdot s(n+γ\tau))
$$

Otherwise `h` can be a vector of length `d-1`, which the decides the weights of each entry directly.

## References

[^Takens1981] : F. Takens, *Detecting Strange Attractors in Turbulence — Dynamical Systems and Turbulence*, Lecture Notes in Mathematics **366**, Springer (1981)

[^Sauer1991] : T. Sauer *et al.*, J. Stat. Phys. **65**, pp 579 (1991)

[^Judd1998]: K. Judd & A. Mees, [Physica D **120**, pp 273 (1998)](https://www.sciencedirect.com/science/article/pii/S0167278997001188)

[^Farmer1988]: Farmer & Sidorowich, [Exploiting Chaos to Predict the Future and Reduce Noise"](http://www.nzdl.org/gsdlmod?e=d-00000-00---off-0cltbibZz-e--00-1----0-10-0---0---0direct-10---4-------0-1l--11-en-50---20-home---00-3-1-00-0--4--0--0-0-11-10-0utfZz-8-00&a=d&cl=CL3.16&d=HASH013b29ffe107dba1e52f1a0c_1245)
