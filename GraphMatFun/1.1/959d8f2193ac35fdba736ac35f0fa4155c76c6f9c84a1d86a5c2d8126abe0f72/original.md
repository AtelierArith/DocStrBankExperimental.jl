```
(graph,cref)=graph_sastre_yks_degopt(k,s,c)
```

Transforms the polynomial evaluation format given by equations (62)-(65) in the reference to `degop`-format. The `graph` is a representation of `y_{k,s}`. Input `c` is a grouping of the coefficients as given by the representation (62)-(65). `c` is a `Vector{Vector{Vector}}` of length `k+1`, representing

```
[
[c_i^{(0,1)}, c_i^{(0,2)}]
[c_i^{(1,1)}, c_i^{(1,2)}, c_i^{(1,3)}, c_i^{(1,4)}, c_i^{(1,5)}, c_i^{(1,6)}]
...
[c_i^{(k,1)}, c_i^{(k,2)}, c_i^{(k,3)}, c_i^{(k,4)}, c_i^{(k,5)}, c_i^{(k,6)}]
]
```

Hence, `c[1]` contains two vectors, the first of length `s`-1 and the second of length `s`. (Note: In the first vector the constant for I is set to zero) and `c[2]` up to `c[k+1]` conatins six vectors: Even-numbered vectors have length `s`+1 Odd-numbered vectors have length j-1, where j is the intex in `c`, e.g., `c[2][1]` has one element and `c[3][5]` have two. For example, equations (57)-(59) are implemented as:

```
c = [
[[c15, c16], [0.0, 0, 0]], # (57)
[[1.0], [0, c13, c14], [1.0], [c11, 0, c12], [c10], [0.0, 0, 0]], # (58)
[[0.0, 1], [0, c8, c9], [c7, 1], [0, c6, 0], [c4, c5], [c1, c2, c3]], # (59)
]
```

**Reference**

1. J. Sastre. "Efficient evaluation of matrix polynomials". Linear Algebra and its Applications, 539:229-250, 2018. DOI: [10.1016/j.laa.2017.11.010](https://doi.org/10.1016/j.laa.2017.11.010)
