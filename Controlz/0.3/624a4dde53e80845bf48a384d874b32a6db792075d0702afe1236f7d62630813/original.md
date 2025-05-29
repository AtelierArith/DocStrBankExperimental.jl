```
K = zero_frequency_gain(tf)
```

compute the (signed) zero frequency gain of a transfer function $g(s)$, which is:

$$
K := \lim_{s\rightarrow 0} G(s)
$$

the zero-frequency gain "represents the ratio of the steady state value of the output with respect to a step input" [source](http://www.cds.caltech.edu/~murray/books/AM05/pdf/am06-xferfcns_16Sep06.pdf)

# example

```jldoctest
g = 5 / (3 * s + 1)
K = zero_frequency_gain(g)
# output
5.0
```

# arguments

  * `tf::TransferFunction`: the transfer function

# returns

  * `K::Float64`: the zero-frequency gain of the transfer function
