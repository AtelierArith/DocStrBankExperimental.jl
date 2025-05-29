```
(graph,cref)=graph_sastre_exp(k,method=:auto)
```

Computes a polynomial evaluation approximating the exponential using `k` matrix multiplications following a `method` given in the reference. The schemes are embedded into `degop`-format, see [`graph_degopt`](@ref).

The methods are (from the paper referenced below):

  * `:ps_degopt`, Paterson–Stockmeyer method embedded into `degopt`-format.
  * `:y1s`, given by equations (34)-(35)
  * `:z1ps`, given by equations (34)-(35) and (52)
  * `:h2m`, given by equations (34)-(35) and (69)

Not all combinations of `k` and `method` are implemented. Available ones are:

  * `k<3`, `method`=`:ps_degopt`
  * `k=3`, `method`=`:y1s`, as per Table 4 in the reference
  * `k=4`, `method`=`:y1s`
  * `k=6`, `method`=`:h2m`, as per Table 11 in the reference
  * `k=8`, `method`=`:z1ps`, as per Table 7 in the reference

The default option `method=:auto` will choose method according to the value of `k`, as prescribed above.

**Reference**

1. J. Sastre. "Efficient evaluation of matrix polynomials". Linear Algebra and its Applications, 539:229-250, 2018. DOI: [10.1016/j.laa.2017.11.010](https://doi.org/10.1016/j.laa.2017.11.010)
